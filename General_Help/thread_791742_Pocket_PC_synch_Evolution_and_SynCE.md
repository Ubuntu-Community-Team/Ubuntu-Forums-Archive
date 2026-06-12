---
title: "Pocket PC synch Evolution and SynCE"
date: 2008-05-12
forum: General Help
---

### Post by spnoe on 2008-05-12
I have followed a How to, on enabling the sync of my Pocket PC and Evolution but I get stuck on what appears to be an error
synce-serial-start was unable to find the file /usr/etc/synce-serial.default:

Please run the synce-serial-config tool to create this file before running this
script again.
I have tried re-installing the necessary software but keep getting the same message. Could someone help me to resolve this problem.

I am running Mobile 2003 and Hardy Heron.

Thanks,
Steve

---

### Post by eternalnoob on 2008-06-05
Hi spnoe,
which how to were you following?
I followed this one
[http://ubuntuforums.org/showthread.php?t=30936](http://ubuntuforums.org/showthread.php?t=30936)
and it worked perfectly for ubuntu 8.04 and Win 2003 SE

did you type in a command like this to configure your USB connection?
> sudo synce-serial-config ttyUSB0

On my computer ttyUSB0 is the USB connection for my PDA

you can find the correct value for your computer by plugging in you PDA and typing dmesg in a terminal
> dmesg
[ 7947.059634] ipaq 3-2:1.0: PocketPC PDA converter detected
[ 7947.062197] usb 3-2: PocketPC PDA converter now attached to ttyUSB0
[ 7947.062552] usbcore: registered new interface driver ipaq

hope this helps

---

