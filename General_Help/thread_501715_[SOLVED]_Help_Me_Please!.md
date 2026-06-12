---
title: "[SOLVED] Help Me Please!"
date: 2007-07-15
forum: General Help
---

### Post by Ian505 on 2007-07-15
Okay, I consider myself fairly computer savvy, but linux and hardware are unknown territory for me. I installed Ubuntu linux on my pc when I got a new drive.Installation was a bit confusing but I managed. It worked fine, but my enthusiasm was burnt when I found out the only way that I could run some of my windows games was through wine which I didnt care to mess with.  I wanted to uninstall Ubuntu because I wouldn't be using it. I looked for a way to uninstall it from the CD and Ubuntu itself, however, I couldnt find one so I simply removed the partitions from the drive that I put it on through Windows and reformatted them to fit my windows needs. Then I did some tinkering on Win XP and had to restart it after I modified a system theme in windows. Then I got something I have not gotten before ever.

GRUB stage1.5.

GRUB Loading, please wait...
Error 17

Looking up error 17 it turns out that its not reconizing the partition- which makes sense considering I reformatted in NTFS. So I got an idea- remove the former linux drive and it will be forced to only look at the drive that contains Windows and I can fix it from there---BAD IDEA, now I get error 21 which means drive not reconized. CAN SOMEBODY PLEASE HELP ME! I am desperate.

(I am currently on older pc while writing this.)

---

### Post by merlinus on 2007-07-15
Boot from xp cd into recovery mode.

fixmbr

-merlin

---

### Post by bernied on 2007-07-15
You need to use your windows cd, or a free alternative like FreeDOS, to reinstate your windows master boot record (mbr). The application is called fixmbr, if I remember correctly.

---

### Post by Ian505 on 2007-07-15
1 problem- I looked for my win cd and couldnt find it.... and did you say REINSTALL?

Is that the only option because I have about 50GBS of important images and files on the same partition windows is on....

---

### Post by Feba on 2007-07-15
No offense, but if you didn't know that Ubuntu wouldn't play Windows games, you're not really computer savvy ;)

As to the thread, this is just GRUB, a bootloader, getting angry at you. GRUB says "HEY. HEY. THERE'S THIS THING IN MY FILE AND I CAN'T FIND IT! Heeeey! I want my thiiiiiiing back!" 

It's nothing serious. Just follow the above advice- put in your XP CD, select recovery mode, then type fixmbr, and all should be right. Or at least, as right as things can be with Windows.

---

### Post by merlinus on 2007-07-15
No, not reinstall xp, but reinstall the windows boot manager to replace grub.

You can use SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Feba on 2007-07-15
>  problem- I looked for my win cd and couldnt find it.... and did you say REINSTALL?
1- Well, sucks to be you. You're going to have to find it somehow. You might be able to fix GRUB from a liveCD, but XP might bitch at you for that. And no, they didn't say reinstall. Please read the advice people give you, it's very frustrating to see someone totally ignore the most important parts of what you're saying, and have to repeat something, or even make MORE trouble

---

### Post by Ian505 on 2007-07-15
Okay, I read through the information but I am not sure what to do other than burn a file to a cd as a image (which I can do.) Beyond that I am confused, could someone please explain things a little more throughly? I am extremely novice to this.

---

### Post by merlinus on 2007-07-15
Boot from the SuperGrub cd.  Then select the following:

English Super [COLOR=#000000]GRUB[/COLOR] Disk
Windows
Fix Boot of Windows

-merlin

---

### Post by Ian505 on 2007-07-15
Thank you very much. I want to do just that, but all of the download links are dead!

Do you have a direct download link?

Thanks SO MUCH for everyones help so far. Ive gone from panic to (seemingly) almost there.

EDIT---
I did the same thing this guy did on this thread : [http://ubuntuforums.org/showthread.php?t=501328&highlight=Super+GRUB](http://ubuntuforums.org/showthread.php?t=501328&highlight=Super+GRUB)

Quote:
Originally Posted by splintercellguy View Post
Yep, use Super GRUB to reinstall GRUB.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Well I'll be damned, the web page is not loading. I googled it and the same page came up. I'll give it some time and try again later in case the server is temporarily down or something.

Thank you though!
__________________

---

### Post by tgm4883 on 2007-07-15
[http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

### Post by merlinus on 2007-07-15
[sgd_plus_distros/sgd_gparted_system_rescue_001.iso]("http://sgd.howto-linux.de/download/binaries/sgd_plus_distros/sgd_gparted_system_rescue_001.iso") 

Save it to disk.

Then burn it as a disk image (NOT a data disk) at no more than 4x.

-merlin

---

### Post by bernied on 2007-07-15
I found this link:
[http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso](http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso)
On this page:
[http://sgd.howto-linux.de/?section=download](http://sgd.howto-linux.de/?section=download)
It seems to work.

---

### Post by Ian505 on 2007-07-15
Thank you! Burning... I will post whether this worked or not.

---

### Post by Ian505 on 2007-07-15
Yay! Yayayayayayaya! Its Fixed! Thank You So Much Everyone! Thank You!

---

