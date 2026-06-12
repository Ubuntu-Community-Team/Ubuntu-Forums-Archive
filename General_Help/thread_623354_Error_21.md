---
title: "Error 21"
date: 2007-11-25
forum: General Help
---

### Post by Untame_Zerg on 2007-11-25
I am fairly new to Ubuntu. As far as I know, I'm running Feisty.

I tried to upgrade my hard drive from a 10GB that I put Ubuntu on just to experiment with. I took that drive out, and it seems like Ubuntu put something on my main HDD with Windows that keeps the computer from booting without the drive with Ubuntu. During startup, I get "GRUB Error 21; disk does not exist".

How can I upgrade from my 10GB? I cant take it out and put in a new 200 to transfer files over to from my 120. I want to use my 120 for Ubuntu, but this is keeping me from doing that. How do I stop the error 21?

Thanks.

P.S.
Is it still possible to use Xfire (an instant messaging/game tracking program) on Ubuntu?

---

### Post by Untame_Zerg on 2007-11-25
Surely someone must know?

---

### Post by Boelcke on 2007-11-25
Surely, someone does know.  Sadly, it really isn't me.  ;)

You've got GRUB, the bootloader, on the main hard drive.  When you replaced the second drive, it got all confused because it didn't find the drive it expected.

You could have Windows put its bootloader back in place:
[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

You could edit GRUB per these directions, and point it to the new drive:
[http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade](http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade)

I'm thinking, though, if you're doing a fresh install of Ubuntu on the new drive (in which case, I'd go ahead with Gutsy, not Feisty -- might as well be current), I wonder if you just boot off the CD, if it'll re-setup GRUB for you anyway?

Can you boot the liveCD with that new drive in place?

---

### Post by Tyke91 on 2007-11-25
you should put the new hard drive in place, then install feisty or gutsy (whatever version you want) onto it.

you will need some sort of external hard drive or something for the file transfers (if you have a windows hard drive that stays in there, you can use that too)*, but the entire procedure should look like this.

1. transfer your personal files from the 10gb hard drive to the holding space (the windows or external)

2. put in the 120 and install ubuntu from the live CD (this will fix your booting problem)

3. transfer the files from the external hard drive (or windows hard drive) to your ubuntu home folder.

------------------------
* if you want to write to your windows hard drive, you will need a program called ntfs-3g [note that Ubuntu 7.10 Gutsy Gibbon has it pre-installed].  to get it, type this command into your terminal in ubuntu

```
sudo apt-get install ntfs-3g
```once you have it, you can copy and paste the files you want to keep directly onto your windows drive, then when you are done, copy them back.

---

### Post by Untame_Zerg on 2007-11-26
Thanks for the help! I went into the recovery console and did the "fixmbr" command, and all is working fine now!

Thanks again!

---

