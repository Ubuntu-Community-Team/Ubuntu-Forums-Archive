---
title: "ubuntu locking up"
date: 2007-11-18
forum: General Help
---

### Post by detoj on 2007-11-18
I've been noticing that lately my system has been freezing repeatedly, sometimes to the point where I'm rebooting several times in less than an hour.  Nothing responds; not the programs, gnome, etc.  Ctrl-alt-backspace doesn't work to restart X, and once the SysRq key didn't work when I tried to reboot the computer.  I can't think of any programs I installed recently that would cause this, nor any changes I made to any files.

Anyone have any suggestions to fix this, or know of any tools or programs I can use to find out what my computer is trying to do at the time it freezes?  Please?

Thanks for your help!

---

### Post by Sef on 2007-11-18
It could be a bad motherboard.   My old computer had a bad memory module unit, and it would freeze up a lot.    To check it out, go into GRUB at start up, and go down to mem86test.   Run it overnight.   If it keeps running, then that will not the problem.   However, mine froze on test 8 repeatedly.

---

### Post by detoj on 2007-11-18
thanks for the suggestion, but I don't think it's my motherboard; I've had this computer for about three years now, two of which were running Ubuntu without any major problems.  I did recently install more memory though, so maybe that's it?  I haven't had any problems with the new memory until now, though.  I'll try running the test tonight in any case, and see what happens.   Thanks.

---

### Post by detoj on 2007-11-19
I finished letting memtest run overnight for about 12 hours.  It was still going in the morning, so I guess that's not the problem.  Just in case though, here's what the test showed at the time I stopped it:

cached: 1279M
RsvdMem: 257M
MemMap: e820-Std
cache: on
ECC: off
Test: Std
Pass: 16
Errors: 0
ECC Errors: --

I'm assuming this is good since there's no errors, but I've never used the memtest before, so I'm not positive.  If the memory is not the issue, is there any way for me to find out what is?  thanks.

---

### Post by wembly6 on 2007-11-19
I'm having exactly the same problem after upgrading to 7.10. Random freezing, sometimes only minutes after booting up. Nothing obvious as to the cause. Sometimes in firefox, sometimes thunderbird, sometimes just on desktop. I have noticed that my cpu usage under system monitor is showing 95% or more most of the time, even with nothing running. When looking at processes there is nothing obvious that is using up the CPU, or memory.

---

### Post by Mithrilhall on 2007-11-19
When it freezes try the following:

```

ctrl+alt+f2

```

Kill Xorg and issue a startx (for KDE) or whatever it is you Gnome people use.

---

