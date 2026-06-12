---
title: "Problem with installation settings, please help"
date: 2013-01-10
forum: General Help
---

### Post by rikonor on 2013-01-10
Hello,

I am a noob in linux and trying to learn.
I recently installed ubuntu 12.10 through a web installation on my laptop.

My harddrive has 500GB.
In the installation process I went along with a default setting:
ubuntu installation size: 18GB.

Now when I try to install a new program which requires 5GB on ubuntu (matlab), it says I only have 471MB left, and therefore cannot install.

I ran Gparted to check the situation and this is what I have:
/dev/sda1 i think this is the dual-boot thingie, has 100MB
/dev/sda2 i think this is the windows 7 partition has 244GB
/dev/sda3 i would think this is where linux is installed but it is NTFS, and from my understanding linux partitions are not NTFS.
unallocated 1MB have no idea what this is.

running in terminal du plus some settings to find big files found what i believe is the linux installation it is in
/host/ubuntu/disks

I am sorry for the lack of understanding, I am looking to understand how to manage my harddrive space on linux and what is considered good practice and also how to be able to complete a succesful installation of matlab.

Thank you very much,
Or

---

### Post by mlentink on 2013-01-10
If you have used a "web" install, you have used the Wubi Windows installer. Wubi does not perform a real dual boot install, but rather installs Ubuntu inside a big Windows (NTFS)-file. This has the advantage of being able to use the Windows add/remove programs functions to delete Ubuntu, but has the disadvantage of limited space. For this reason, some argue that a Wubi install is best suited to try Ubuntu out for a limited period of time. 

If you would like to think about a real dual boot install please refer to the installation wiki here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Impavidus on 2013-01-10
Yes, this must be a wubi install. Wubi installs are limited to maximum 30GB in the "linux partition". If you want more, you'll have to do a true dual boot (or ditch windows, but as linux noob (your words) you're probably not ready to do so). It's not difficult, as I've seen you only have three partitions and (presumably) plenty of free space on your disk.

The 100MB /dev/sda1 is your windows boot partition, which is standard nowadays on windows.

---

### Post by rikonor on 2013-01-10
Thank you, you're right - I did do a wubi install. 
You cleared it up for me, I will try and do a fresh install from a CD soon.

Thanks again,
Or

---

### Post by rikonor on 2013-01-10
I was also wondering - since mine is currently a wubi install, could it be that it affects performance? I've been feeling as if ubuntu is running a bit slower then I would expect on my computer.
I mean, especially I'd expect it to run smoother then windows, but I don't think thats the case for me.

Again, thanks for the help.

---

### Post by Impavidus on 2013-01-11
I understood that win7 is quite fast for a windows system. I've never tried myself, I'm using 100% ubuntu after I found out I couldn't understand win XP.

Maybe you have to check your graphics drivers. Bad graphics drivers can slow down your system.

---

