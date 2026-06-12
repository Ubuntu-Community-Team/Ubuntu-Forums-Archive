---
title: "Ubuntu and Vista help!!!"
date: 2007-11-24
forum: General Help
---

### Post by lupo92 on 2007-11-24
Alrightly, here is the problem. I have partitioned my hardrive into two different sections, using G-parted. One section contained Windows Vista Ultimate, and the other contained Windows XP. When I booted up my computer, it always gave me a choice of selecting which partition I wanted to run. All was well. However, I deleted the XP partition, and installed Ubuntu in its place. I installed everything correctly, making sure both partitions still were intact. Yet, now when i start my computer I do not have any option of selecting which partition I would like to run, and it automatically boots Ubuntu. HOW DO I FIX THIS PROBLEM SO I CAN BOOT VISTA? I need help fast please! I am desperate....

BTW: I also tried this link:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

It almost worked, except for when I restarted the computer, it said the Windows portion did not exist,so does some of the data has to be changed for it to work? I do not know, I am new to this...But I know Vista is still there, I just can not get it to boot...

Thanks!!!

---

### Post by Craigus on 2007-11-24
Supergrub should be able to fix it for you:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by lupo92 on 2007-11-24
Thanks, I'll try it out now...Looks as if it might work.

---

### Post by Multi-Booter on 2007-11-24
Yeah, it's no problem really... you just need to edit your grub to include vista as a boot option... and tell grub "where" to go load it from, which sounds like hd(0,1)...

Then you will be able to select it and boot it once you do those two things...

---

### Post by lupo92 on 2007-11-24
The Super Grub didnt work. It made matters worse when I started playing with it but than i fixed the error i had made. Anyway, when I try to boot windows it just keeps saying booting...How long am I supposed tow ait? I waited 3-5 minutes and it didnt boot, and when I tried it a second time, the same thing happened.I followed all the instructions, and even read them on the site before I used the program, and I even used the guide while I used the program so I am 90% sure I did everything I was supposed to do, but still no result...

Should I just delete my Vista Partition, and reinstall Vista? That would be a big pain...

Also, when I tried to run it from a partition is said the Vista was in (hd0,0) [O have dots in the middle] which is the same root as the Ubuntu. Any ideas on what I should do? I really need to get back on my vista, and the worst part is if I have to reinstall it, I lost my installation disk...:mad::mad::mad::mad::mad:

Thanks for your help!

---

### Post by Craigus on 2007-11-25
Can you post the comtents of ubuntu's /boot/grub/menu.lst ?

---

### Post by mikeym on 2007-11-25
Just to explain what is happening to you so you don't worry that you've lost your Vista partition. When your computer boots from a disk it first looks for a Bootloader (a program for telling the computer which partition to start loading and where to find the data to start loading on that partition). This boot loader is normally stored outside of either boot partition in a section called the Master Boot Record (MBR). The screen you are used to looking at what gives you a choice of whether to load Vista or XP is windows bootloader. Linux being Linux there is a choice but the most used and therefore best for your purposes is GRUB. Supergrub is a program for configuring it. What it should allow you to do is to tell GRUB where to start loading Linux of one partition and where to start loading Windows of the other. 

So don't worry everything is still there on both your partitions and wont need reinstalling it's just a matter of sorting out your bootloader.

---

### Post by lupo92 on 2007-11-25
I know that, but Super Grub will not let me fix the Boot for Windows, and when i try to boot windows from the Super Grub disk, it still doesnt boot. I am still confused on how to fix the problem and what steps i need to take.

---

### Post by Craigus on 2007-11-26
Can you post the contents of ubuntu's /boot/grub/menu.lst ?

---

