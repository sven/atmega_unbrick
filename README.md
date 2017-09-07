# Unbrick My Atmega

## Story

Sometimes my ATmega328(P) aka Arduino Nano isn't accessible via USB anymore
after flashing. To recover it an [USBasp](http://www.fischl.de/usbasp) and some
special AVRDUDE parameters are needed.


## Recover Atmega328P via USBasp Programmer

First repeat this command until it succeeds:

```Shell
avrdude -v -patmega328p -cusbasp -Pusb -e -Ulock:w:0x3F:m -Uefuse:w:0xfd:m -Uhfuse:w:0xDE:m -Ulfuse:w:0xFF:m -u -B10 -F
```

Then use this command until the bootloader is successfully flashed. After that
there is a good chance that the onboard USB programmer works again.

```Shell
avrdude -v -patmega328p -cusbasp -Pusb -e -D -U flash:w:ATmegaBOOT_168_atmega328.hex -F -u -B10
```
