---
title: "Help!  / filling up! input irq status -75 received"
date: 2007-03-08
forum: General Help
---

### Post by xadder on 2007-03-08
Hi!

My / is filling up with messages, kern.log and syslog files, all saying:

Mar  8 15:29:01 saturnus kernel: [17179766.448000] drivers/usb/input/hid-core.c: input irq status -75 received

and being added at a very fast rate! How can I stop this?!

I'm running edgy, and just now don't have any usb stuff attached.

Help!

---

### Post by sbassett on 2007-03-08
Do you happen to have a usb mouse?

---

### Post by xadder on 2007-03-08
Not a mouse, by I am using an IBM usb keyboard (have been using it for months). I've just checked the cables (all I cound think of!), but seems okay. And the keyboard is working as I type this.

---

### Post by sbassett on 2007-03-08
I have been checking around. It appears that the error is non-fatal (as you can still use the device) but it attempts to send almost what would be considered an overflow of signal. Unless we get an update soon, you might wish to report this issue at launchpad. I believe there has been even talk of removing the -75 response due to it's trivial nature (apart from filling up people's hard drives). Sorry I couldn't be of more help.

---

### Post by xadder on 2007-03-08
Thanks anyway. Good to know that it isn't too serious, as long as I keep an eye on /

Strange that error or warning messages  are allowed to fill up the most important disc!

---

### Post by xadder on 2007-04-27
SOLVED:

 - it disappeared for me after I upgraded to fiesty :)

---

