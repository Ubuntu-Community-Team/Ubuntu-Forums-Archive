---
title: "Fatal X error in Xubuntu"
date: 2007-02-02
forum: General Help
---

### Post by herold on 2007-02-02
I have been trying to install Xubuntu on an old computer, and have not gotten it to run.  I gave details in a previous post, which I have copied below, with lots of people looking at it but no responses.  (Thanks for looking at it.)  Since then, I installed xubuntu 6.10 alternate on a different computer, identical to the first one, to try to eliminate the possibility of defective hardware (but I am using the same monitor, an old Sun 21" crt).  I also looked at several logs after starting xubuntu in recovery mode.  In /var/log syslog, I got the messages "init: tty1 process killed by request 15," (this was repeated 6 times, with the tty1 being incremented to tty2 ... tty6), "Failed to start x server several times in a short time period; disabling display," followed by "exiting on signal 15."

I  installed xubuntu 6.10 alternate i386 on an old Digital Venturis FX-2 that runs at 166 Mhz, has 128 MB Ram and a 2 GB hard drive.  Installation seemed to go well until it rebooted at the end of the installation.  Then after the xfce rodent screen, the screen blanked, the cursor went to the upper left side of the screen, and the monitor went dead after about five seconds.  The same thing happens after a "normal" boot.  If I hit ESC after the rodent screen and select the recovery mode, xubuntu starts in bash.  I do not recognize any problems here.  I can use bash.  But when I type startx, I get the blank screen with the blinking line cursor at the upper left corner of the screen, and after about five seconds the monitor goes dead, or at least in something like a sleep mode.  What is going on here?  Do I have a hardware incompatibility, or some other problem?  Any suggestions?  (Before I tried the "alternate" CD, I tried the xubuntu 6.10 "desktop" CD, and installation seemed to hang shortly after the first rodent screen.  Maybe it was due to the same problem, rather than a bad download for the CD.)

---

### Post by herold on 2007-05-05
I'll reply to my own post.  I see that many people have read my post, but no one responded.  Thanks to all who read it.
I tried replacing Xubuntu Edgy with Xubuntu 7.04 when it was released.  Still didn't work.  I had been suspecting that ACPI was the source of the problem.  I tried editing GRUB previously, but no luck.  I had been putting "acpi=off" on a separate line, but somewhere ran across the advice to put it at the end of a line starting with "kernel."  I did so, and that seems to have been the problem.  Xubuntu now runs on the old DEC Venturis computer.

---

