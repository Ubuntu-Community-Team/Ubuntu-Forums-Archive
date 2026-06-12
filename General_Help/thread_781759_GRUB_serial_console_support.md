---
title: "GRUB serial console support"
date: 2008-05-04
forum: General Help
---

### Post by oliver341 on 2008-05-04
My dedicated server provider uses the serial console output of lilo as a means of monitoring the boot process. I would like to switch to GRUB.

I read [here]("http://orgs.man.ac.uk/documentation/grub/grub_7.html#SEC29") that I should type these two lines into a GRUB console:

grub> serial --unit=0 --speed=9600
grub> terminal serial

But when I run this command in a grub console I get this:

```
grub> serial --unit=0 --speed=9600
serial --unit=0 --speed=9600

Error 30: Invalid argument
```

What's invalid and why? Output of help:

```
grub> help serial
help serial
serial: serial [--unit=UNIT] [--port=PORT] [--speed=SPEED] [--word=WORD] [--parity=PARITY] [--stop=STOP] [--device=DEV]
    Initialize a serial device. UNIT is a digit that specifies which
    serial device is used (e.g. 0 == COM1). If you need to specify
    the port number, set it by --port. SPEED is the DTE-DTE speed.
    WORD is the word length, PARITY is the type of parity, which is
    one of `no', `odd' and `even'. STOP is the length of stop bit(s).
    The option --device can be used only in the grub shell, which
    specifies the file name of a tty device. The default values are
    COM1, 9600, 8N1.
```

The help text appears to indicate my syntax is correct. Am I doing something wrong? Help appreciated.

---

### Post by tristezo2k on 2009-09-14
It is very probable that you are putting this stanzas within the title part.
You must use them before any title part.
Say at menu.lst
something
otherthin
morethigns
serial --unit=0 --speed=9600
terminal serial
( and then)

title MySerialKernel
root (hd0,0)
kernel /there/kernel and so on.
initrd /here/is/my/initrd

Regards.


[QUOTE=oliver341;4879956]My dedicated server provider uses the serial console output of lilo as a means of monitoring the boot process. I would like to switch to GRUB.

I read [here]("http://orgs.man.ac.uk/documentation/grub/grub_7.html#SEC29") that I should type these two lines into a GRUB console:

grub> serial --unit=0 --speed=9600
grub> terminal serial

But when I run this command in a grub console I get this:

```
grub> serial --unit=0 --speed=9600
serial --unit=0 --speed=9600

Error 30: Invalid argument
```

---

