---
title: "Serial communication too slow"
date: 2014-12-01
forum: General Help
---

### Post by joachim3 on 2014-12-01
Hi everyone,

I'm a bit new to ubuntu (and linux in general) so I'll try to do my best ;)

I have a serial link between a microcontroller and my laptop. (from UART to /dev/ttyUSBx)
I need a very (I mean Very ;) fast link between the 2 to plot a few graph and variables with matlab. 
Everything works perfectly on windows with a baudrate of ... 1.000.000 (in fact, it works like a charm at 1.500.000 as well)
On ubuntu, the message seems incomplete (every msg should start with 4 specific char) which makes me believe that the buffer is overflowing...
It works fine at a baudrate of 115.200

It is the same laptop, same cable, same microcontroller, same user : me (if it is relevant ;) ) and I never tried during full moon ! (ok, I'm out  ========>  )

I'm using LTS 14.04.

Is it something known with 14.04 or others? Is there a fix/workaround ?

Thanks for the help !

---

### Post by tgalati4 on 2014-12-01
It's possible that the module that controls the UART chip can only support 115K baud, but the Windows driver uses a proprietary and hidden feature that supports a faster speed.

What is the make and model of the motherboard and UART chip?

---

### Post by joachim3 on 2014-12-03
My laptop is an Asus g74sx (i tried to find the exact MB but couldn't find it. I'm not at home for the moment)
on the MCU side, it's a PIC32mx250 

you say "it is possible that the module that controls the UART chip..." You mean on the microcontroller side ? Because then I'm sure it can ( according to the manual and datasheet)

---

### Post by tgalati4 on 2014-12-04
No, the laptop side.  If the kernel module only supports 115k baud (maximum) then that is your limitation.

You can play with *setserial*, to see if you can get a faster speed:

```
man setserial
```

> tgalati4@Mint14-Extensa ~ $ sudo setserial /dev/ttyS0
[sudo] password for tgalati4: 
/dev/ttyS0, **UART: unknown**, Port: 0x03f8, IRQ: 4


Simply setting the UART chip (since there is no plug-and-play with serial devices) may unlock faster speeds.

>        uart uart_type
              This  option  is used to set the UART type.  The permitted types are none, 8250, 16450, 16550, 16550A, 16650, 16650V2, 16654, 16750, 16850,
              16950, and 16954.  Using UART type none will disable the port.


---

### Post by joachim3 on 2014-12-09
Thanks for the info.

I tried with another MCU (much more powerful) and was able to transmit at 1.0M 
Good news is, the kernel can go faster than 115k. Bad is, without an actual logic analyzer, I'll never know for sure what is happening. I believe the clock error is bigger with the first mcu and windows may be a bit more tolerant than linux. Apart from that, I'm out of idea ;)

---

### Post by tgalati4 on 2014-12-09
If you are using a USB-to-serial converter, then you need to consider the limitations of the USB-to-serial converter chip inside the cable.  A common one is a PL2302.  It's possible that Windows has a better driver for the USB-to-serial converter than linux.  What converter are you using?

---

### Post by joachim3 on 2014-12-10
The PL2303HXA. By datasheet : baudrate : 75 ~ 6M bps

---

### Post by tgalati4 on 2014-12-10
```
modinfo pl2303
```

You can turn on debug mode and see what the errors are at higher speeds.

---

