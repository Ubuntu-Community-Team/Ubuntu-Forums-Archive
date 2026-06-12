---
title: "i want ubunto, but i can't uninstall suse's grub!!"
date: 2006-08-26
forum: General Help
---

### Post by kossel on 2006-08-26
i'm kind of newbie in linux, so u may need some patiant

I have windows xp pro and suse 10.0 grub dualboot. but know i want to try ubuntu.
but i read in some forum, they said that i must rewrite the MBR in order to uninstall grub, so i can boot windows, and then, delete teh suse partition.

my problem is: i used freeDos, winxp disc, i did the fdisk /mbr or fixmbr. but after that, the computer starts, and stop at a black screen, look like it was trying to boot a system. i installed ubuntu, and i neither can see a dualboot screen. what can i do? does ubuntu install some booter like lilo or grub?? how can i change my suse into ubunto and keep win xp?

PS: sorry about my english

thanks

---

### Post by LadyDoor on 2006-08-26
Ubuntu installs grub. As long as you didn't delete your windoze partition (I think you would've known if you had) you can set it up to dual boot again. Edit **/boot/grub/menu.lst**; in there you should find some useful comments on dual booting. You might also search on these forums for "set up dual boot" or something along those lines. Good luck!

--Door

---

### Post by ifokkema on 2006-08-26
I'm not too sure from your story if you can get into Ubuntu now.
Try running
```
sudo update-grub
```
It should find your Windows, and add it to the list of choices.

---

### Post by kossel on 2006-08-26
let me tell you what did i do, i think it could help u understand me

1. i had winxp and suse 10.0 grub dualboot, and works well.
2. i want to change suse into ubuntu, so, i download freeDos (i also tried ultimateboot cd) to book the pc.
3. when i m in freeDos/ultimatebootcd (UBC) i type fdisk /mbr and fixmbr
4. i insrted ubuntu disc, and installed it, obviously i format suse partition and resized is to 40 gb ext3, and 2gb linux-swap
5. after ubuntu installation, i restarted the pc.
6 then, nothing happend to my pc, black screen with a " _ " in the screen, looked like it was trying to boot.

so. i had to reinstall suse to ge my pc boot, and making posts here :biggrin:

---

### Post by kossel on 2006-08-26
but i still want ubuntu..

---

### Post by kerry_s on 2006-08-27
Skip the fix mbr stuff and just pop the ubuntu cd in and install. Are you sure you got a good burn on your ubuntu cd, use the check disk.

---

### Post by peabody on 2006-08-27
> **kossel said:**
> let me tell you what did i do, i think it could help u understand me

1. i had winxp and suse 10.0 grub dualboot, and works well.
2. i want to change suse into ubuntu, so, i download freeDos (i also tried ultimateboot cd) to book the pc.
3. when i m in freeDos/ultimatebootcd (UBC) i type fdisk /mbr and fixmbr


Okay, that's your problem right there.  That would fix it for Win98, but I'm pretty sure that won't work for WinXP, at least, the fixboot should be different.  You need to boot a WinXP recovery console and run fixmbr fixboot from there.

---

### Post by kossel on 2006-08-27
hmm

do u think it will works if i skip the fixmbr, and using ubuntu disc to format suse partition then installing ubuntu?
because i dont have the winxp cd :( 

well let me try

brb in 5 hours installing...

---

### Post by peabody on 2006-08-27
> **kossel said:**
> hmm

do u think it will works if i skip the fixmbr, and using ubuntu disc to format suse partition then installing ubuntu?
because i dont have the winxp cd :( 


That's a dangerous world to be living in with dual booting.  Dual booting always has its problems.  It can be impossible to get back to your windows xp if you don't have a recovery CD.  Just try and get a pirate version of the XP disk, as far as I know, all you really need is the recovery console.

---

### Post by Rui Pais on 2006-08-27
> **kossel said:**
> hmm

do u think it will works if i skip the fixmbr, and using ubuntu disc to format suse partition then installing ubuntu?
because i dont have the winxp cd :( 

well let me try

brb in 5 hours installing...

i had a Gentoo grub partition fully working, so i just skip grub installation when i installed Ubuntu and just add an entry for ubuntu on it's menu.lst.

Later on, one can reinstall grub from Ubuntu (but grub is the same for any Linux...)

---

### Post by kossel on 2006-08-28
omg...  last night i skip fixmbr or fdisk /mbr and isntall ubuntu directly, after the installation, i rebooted, and the screen says..

loading grub stats...

loading grub 1.5
error 17...

so i had reinstall suse again so i can boot my pc and making post here :(

i m so tired doing that..  thats my 4th time reinstalling suse and ubuntu..

maybe the cd that was a bad burn cd :S

---

### Post by Rui Pais on 2006-08-28
> **kossel said:**
> so i had reinstall suse again so i can boot my pc and making post here :(

you should keep [these procedures]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub") at hand when it cames to broken grub. No need to reinstall a full distro!

Check a large a good howto on grub [hear]("https://help.ubuntu.com/community/GrubHowto").

[Here]("http://ubuntuforums.org/showthread.php?t=224351") is a good thread on grub installation and problems.

If you want to know what error 17 is do a google search on "grub error 17". Goolgle is full of excellent articles on each Grub error, explanations and solutions.

---

### Post by kerry_s on 2006-08-28
What type of filesystem are you formatting and installing to?(ext2,ext3,reiserfs) Also the default suse install uses a extended partion, make sure you format till there's only the xp partion.

---

### Post by ifokkema on 2006-08-28
BTW, next time you can't boot your new install, just put back in the CD and boot from that. Why reinstall Suse all the time?!!??

---

