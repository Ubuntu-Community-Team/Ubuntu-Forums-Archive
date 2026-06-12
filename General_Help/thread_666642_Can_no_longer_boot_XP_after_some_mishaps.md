---
title: "Can no longer boot XP after some mishaps"
date: 2008-01-13
forum: General Help
---

### Post by ahsieh on 2008-01-13
First off, I have no idea what I'm doing. Trust me, you'll see.

I recently tried to install Ubuntu 7.10 to an external hard drive, following some directions I found online and printed out. Basically what I did was install from the 7.10 Live CD, and then installed it to /dev/sdb1; I also changed the Boot Loader option in the Advanced tab during the Ubuntu install from (hd0) to (hd1), while following the directions.

Then I installed, rebooted, and attempted to boot Ubuntu off of my external hard drive. However, when attempting to do so, I got an "Operating System Not Found" error. So I looked online and I got some more instructions (sorry, I probably should've saved these sites . . . I didn't), and I think basically what I found were directions as to how to install GRUB (or maybe not--I have no idea what I'm doing) on my hard drive. So I followed them, and it *still* didn't work.

Then I decided to bite off of more than I could chew (not that I didn't already) and repeat whatever I did before to different locations [something like (0,0) to (0,1) and (0,2)] and then restarted, hoping my button mashing would lead to something.

After a few more "Operating System Not Found"s, I decided to give up and stick to Windows XP. (Which I hear is blasphemy. I'm sorry, I'll come back when I'm better at this whole Ubuntu thing.) But the problem is, when I tried to boot off my laptop's internal hard drive, it gave me the following error:

Grub Loading Stage 1.5
Grub Loading please wait....
Error 21

It would not boot XP (obviously), and then I had to manually turn off my computer. Now I'm pretty sad.

I'm running the LiveCD of 7.10 right now, as it's the only way I can do *anything* on my computer. I'm sorta getting used to it (I've been out of commission for that long) so if you could help me boot XP AND get rid of my "Operating System Not Found" message . . . well, that would be miraculous, haha.

Thank you so much! I really, really appreciate it.

Andrew, a.k.a. Ubuntu (Ex?)Wannabe

---

### Post by Craigus on 2008-01-13
Have a look at this thread:

[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/")

> YEAH!!!!

I got all of my problems sorted out! Here's what I did...

1)I ran fixmbr from a windows install disk in recover mode to fix the mbr on my internal hdd. This was kinda scary because the little app tells you that the partitions might not be accessible. I don't know what would have happened if I had more than one partition, but it did work with a single partion drive.

At this point, Windows booted as normal. However, trying to boot Linux from the external drive returned error 17.

So, to fix that little bit...

2)I modified the boot drive from hd1,0 to hd0,0 and pressed b to boot linux.

3)Once I was in Linux, I edited the menu.lst file to change all linux entries to hd0,0 instead of hd1,0.

Now, everything works great. If I don't elect to boot from the external drive (automatic internal drive boot), Windows runs automatically. If I do elect to boot from the external drive, grub allows me to select which Linux distro to run.

Thanks again for all the help. I couldn't have got this fixed without you guys!
- Tony


Don't worry, none of us had any idea what we were doing when we were starting out ...

---

### Post by ahsieh on 2008-01-13
Thanks for the info, I'll try that as soon as I find an install disk, haha. Do you think the one for Windows XP Media Center would work for this? Because, ah, that's all I can find. :/

How would I go about modifying the boot drive from (1,0) to (0,0) . . .? 

Thanks so much,
Andrew

---

### Post by Craigus on 2008-01-13
[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html]("http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html")

To install grub with correct options, you could just use the supergrub disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by ahsieh on 2008-01-13
Thanks, but this says I can only run it from Windows; do I just try it through Wine, or what?

. . . okay, so I opened it though Wine and it opened MbrFix.htm, which . . . makes no sense to me. :( I'm sorry! But could you help me through this?

Thanks (and apologies),
Andrew

---

### Post by Craigus on 2008-01-13
> this says I can only run it from Windows

Sorry, should have been more explicit. I would download a windows boot floppy and run it from that:

[http://www.bootdisk.com/]("http://www.bootdisk.com/")

If you have no floppy, you may have to make a bootable CD or do something with bootable USB.

Edit: you may also be able to do this with testdisk, I'm not certain:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by c0met on 2008-01-13
Hi,

Craigus has referred you to the SuperGrub disk. If you download the ISO of this from the site he has given you, and then use it to boot your computer, you will be presented with options. The options are simply to
[LIST]
[*]get the computer to boot from Linux
[*]get the computer to boot from Windows
[*]Get the computer to dual boot
[/LIST]

Select your choice and in 5 secs, the appropriate boot records are fixed and your computer will work. If you choose the incorrect option, it's no drama because you simply reboot using the SuperGrub disk and choose the correct option. SuperGrub has saved me on a number of occasions.

---

### Post by Craigus on 2008-01-13
Good point - I was getting distracted by the fixing mbr issues.

---

### Post by Omnios on 2008-01-13
Grub is in the mbr. The grub info is on your external that you installed Ubunru on and it has to be accessable by grub to boot.

---

