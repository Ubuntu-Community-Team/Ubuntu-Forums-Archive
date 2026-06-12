---
title: "Major Problem - Can't Boot At All !!"
date: 2007-11-03
forum: General Help
---

### Post by LennyGATC on 2007-11-03
Hi,
Here's how I developed my problem. I have a system with Windows XP Pro on it. I have 2 internal drives, a 160 GB and a 60 GB, labels C,I,J for the 160 and K, L for the 60 GB.  'C' is (was) my boot drive.  I also have a 320 GB external drive, labels F,G and H.  I tried the Ubuntu CD Rom and thought I would like to give it a try. I'm not too happy with all the errors and daily problems with XP. I was considering a Mac, but a friend suggested I try Linux first. 

I went out and purchased a second 320 GB external drive solely for the purpose of loading Ubuntu there, to keep it separate from the rest of the system. I went thru all the steps to load Ubuntu on the new drive,  finished the process and restarted the computer. I received an Error : 21 during the boot, GRUB problem at stage 1.5.  At this point, I have no idea what this means.I still don't, but after some checking, I find that my BIOS won't boot from and external USB drive.  Unfortunately, somewhere along the line during the installation, which must have directed the computer, somehow, to boot from the external drive, which it can't, my internal drives have become unrecognizable. The only place I, the computer, can see them, is when I load Ubuntu thru the CD. In the Linux environment, the drive are visible, and accessable, though I can't write to them, nor copy them.

When I tried to setup Windows XP on the internals, after disconnecting the externals, setup couldn't see the drives. I have to assume from this, that the installation process did something almost physical to the drives, but I imagine software related.

The bottom line is, I can't boot my computer, my files may be lost, and something that was supposed to make life easier just increased my stress and anger level 10-fold.

I know this is long-winded, but I wanted to supply as much info as possible to allow a basis for anyone that could possibly help.

Thanks,
Lenny G

---

### Post by rickdog on 2007-11-03
First of all, I 'd like to say, don't freak out man! I've been there before and with the help of these forums and people's suggestions, you'll probably be out of hot water soon.

Anyway, it does sound like you got yourself into a pickle, and the first thing I'd probably do would be to look up the Super Grub Disk on google and burn me one and see if it did the trick. It has saved me before, maybe it'll work.

If nothing else works, don't worry, you shouldn't have lost any files, I'd just disconnect all externals, and reinstall Ubuntu on a small portion of one of the internals and let it do it's thing about discovering the OS on your system and configuring grub to it. Then you can use NTFS3g to access the windows drive and recover your files. Basic installs only take about 40 minutes anyway.

That's all I got for now... Good luck.

---

### Post by LennyGATC on 2007-11-03
Thanks, I'll give it a try and get back to you.

Lenny G

---

### Post by LennyGATC on 2007-11-03
Hey Rickdog,

Of course I freaked out, and then taking your advise, I downloaded Super Grub. It took a while to get it on a bootable disk (read ALL !! the instructions, no time), but I did, went thru the steps, and my computer is now working as normal as it can.  THANKS for your HELP !

Lenny G

---

### Post by rickdog on 2007-11-04
Sweeeeeeet.

---

