---
title: "problem with installing wubi"
date: 2008-06-15
forum: General Help
---

### Post by iaragorn on 2008-06-15
Hello all,

I have tried install ubuntu-8.04-beta-desktop-amd64. And I have following problems. 
First problem touched I have multiple hard drives, so I have booting problem (no booting record found or something like that), but I found solution on 
(
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)
Booting problems: Error 15, file not found
Do you have multiple hard disks?
...
)
It helps. But next problem started. When booting the first screen displays (logo ubuntu), after some time black screen appears and that's all. Nothing happen. When I tried recovery console, I get 
menu with 3 choices 
1 - resume normal boot (again black screen)
2 - command line (I don't know what to do there???)
3 - reparation of some king Xserver or something, it change anything

Could somebody help?
Thanks

---

### Post by ago on 2008-06-16
Look into /var/log/syslog from recovery console, it might be that you need to install a video driver

You can try to set the video driver to vesa for the time being

---

### Post by iaragorn on 2008-06-16
Hello 

1 - in the syslog was absolutely nothing

2 - I have no idea how to set video driver

3 - when I am using recovery console I have following problem. When enter the command line I got following lines on the screen:

54.549008 RIP touch_dirty_limit+0x51/0x90
54.549078 RSP<fffff81063f625ab8>
54.549582 BUFFER I/O Error on device loop, logical block 393217. lost page due to I/O error on loop)
54.549677 BUFFER I/O Error on device loop, logical block 393217. lost page due to I/O error on loop)
etc. ....

Any idea?

Thanks

---

### Post by Grimm310420 on 2008-06-16
how do u make a new topic lol?

---

### Post by iaragorn on 2008-06-17
So I make some step forward.

I reinstall whole ubuntu, then I start recovery console and in the shell prompt i run this command
sudo dpkg-reconfigure xserver-org and it helps, now it is not freezing after black screen.
Now it is freezing with this message: "Loading ACPI modules"

Any idea what to do?

I don't know guys, but I already spend 1 week with installing ubuntu and result is still nothing. I'm starting understand why is windows so popular.....

---

### Post by ago on 2008-06-17
set acpi=off as kernel parameter in c:\ubuntu\disks\boot\grub\menu.lst

---

### Post by iaragorn on 2008-06-20
Thanks for answer.

Finally I used intel-ubuntu release instead ubuntu-8.04-beta-desktop-amd64
and it is really working fine (all problems have gone).
This answer I am writing from Ubuntu :popcorn: YUPIIIIIIIIIIIIIIIIIIIIIII

Anyway thanks for help

---

