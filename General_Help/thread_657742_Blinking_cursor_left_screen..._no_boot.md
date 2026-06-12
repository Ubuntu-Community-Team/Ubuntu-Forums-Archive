---
title: "Blinking cursor left screen... no boot"
date: 2008-01-03
forum: General Help
---

### Post by daver2u on 2008-01-03
Kubuntu Hardy
kernel 2.6.24.2.6-Generic
After Grub loader -- i had a cursor blinking on the left corner of the screen.
alt-control-F1 (F2,F3 etc) didnt work.
I verified the system was booting by connecting to the machine via FTP (I couldnt get a command line to verify this)

Using the recovery option in the GRUB menu I was able to load a command prompt.
I followed troubleshooting procedures for Xorg to no avail.
when I used /etc/init.d/kdm start it would load the blinking cursor so alt-control-f1
the error was usplash was unable to find a them... odd
then randomly I typed sudo apt-get install kdm
which generated the error message that dependency libc6-i686 was needed and not installed
so i typed sudo apt-get install libc6-i686

rebooted and the system came up...


please forgive my lack of grammar and sentence structure.


shouldn't there be something in place to prevent required packages from becoming removed

---

### Post by SOULRiDER on 2008-01-03
I dont really know what to say about your problem other that:

Hardy is alpha, dont use it :P
Ask in #ubuntu+2 on irc.freenode.net

---

