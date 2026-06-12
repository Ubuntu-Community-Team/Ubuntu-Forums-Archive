---
title: "laptop freeze, upper-case light blinking"
date: 2008-05-15
forum: General Help
---

### Post by cseljatib on 2008-05-15
Hi there,
i am using ubuntu 8.04 in a lenovo t60.

the problem:
sometimes when i am working (does not matter in what program), the light of the CapsLk at the bottom of the laptop-screen (the one that shows "A", and is on when you hit once the CapsLk key, and is off when you hit again) start to blink, and the laptop just freeze, showing either a black screen or the screen that i was seeing before of the freezing.

What can i do??,
PLEASE help!!

thanks

---

### Post by gasparov on 2008-05-15
Can't really help you but its a kernel panic when the caps lock starts blinking

At least now you now what to fix :D

---

### Post by lunatico on 2008-05-19
> **gasparov said:**
> Can't really help you but its a kernel panic when the caps lock starts blinking

At least now you now what to fix :D

What do you mean with "At least now you now what to fix"???

What to fix? Where to look to what's causing it?

Cheers!

---

### Post by eldragon on 2008-05-19
ive had kernel panics in the past. they resolved to a faulty sata cable.


first thing:
did this started happening for no reason? or did this start rigth after an OS upgrade? (or kernel upgrade?)

chances are an upgrade broke a kernel module.

if this started happening for no reason, i would check for ram with memtest (you should have an option with any live cd. leave it running for a while (24Hs?)

they i would check the hdd for defects. downlad the ultimate boot cd from [www.ubcd.com](www.ubcd.com). it has lots of apps to troubleshoot these kind of hardware problems. including manufacturers diagnose apps for hdds.


if you did a kernel upgrade. press esc when prompted at grub. and pick another kernel, see if that fixes it.

if you didnt do a kernel upgrade. disable any kernel module that could be causing trouble. (closed source binary blobs. start with wireless and display, if they apply....)

thats all i can think of, kernel panics are kind of difficult to troubleshoot.


good luck

---

### Post by lunatico on 2008-05-20
Thanks for the hints. I'll go for an extensive hardware test, but Windows works fine (no BSODs) so....
And this happens every once in a while, like once a week at most, and under no specific reason, and usually when I'm not in front of the computer.
To bad there is nowhere to look like a log or something.

Cheers!

---

### Post by eldragon on 2008-05-20
the kernel logs stuff in /var/log/kern.log

search there for anything unusual. althought i dont know much about analyzing it, maybe if you post its contents here, someone else could give you a hint

good luck

---

### Post by jshayden on 2009-10-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300693?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300693?comments=all)

---

