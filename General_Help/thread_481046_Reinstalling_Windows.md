---
title: "Reinstalling Windows"
date: 2007-06-22
forum: General Help
---

### Post by TreeFinger on 2007-06-22
Yes, I am making this thread :p

Well I like to play counter-strike 1.6. I can't do that on Ubuntu right now, I have a 6 year old PC with 512MB of ram and I know that won't be playing cs on Ubuntu very well. About 3 days ago my steam just completely stopped working. It will be in processes but it will not show the steam icon anywhere on my desktop. Steam Support pretty much sucks. They don't care about 1.6 anymore because they want people to buy/play source to make money. I have tried everything they say on their support answers to try and nothing has worked. My only option is to reinstall windows. 

Right now I have Ubuntu and Windows installed on separate partitions. I want to reinstall windows. I have never done this before with a dual boot so I am wondering how I will be doing it. How can I format one partition? Can I do it from my Ubuntu partition? That would make things a lot easier.

I know last time I formatted my entire hard drive I installed Ubuntu first and microsoft 2nd. This caused problems with my boot loader. Will the same be true if I just format the partition with windows on it currently and reinstall? Thanks for any responses. ( I try to keep the M in microsoft uncapitalized and the U in Ubuntu capitalized because Ubuntu is superior :o )

---

### Post by mikewhatever on 2007-06-22
Reinstalling Windows is a relatively simple task, sort of like installing Ubuntu with an alternate cd. Use the guide to help you [http://theeldergeek.com/xp_pro_install_-_graphic.htm](http://theeldergeek.com/xp_pro_install_-_graphic.htm)

The installation overwrites the part of GRUB in the MBR, so that you'll only be able to boot Windows. Use yet another guide to reinstall grub using Ubuntu live cd
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by TreeFinger on 2007-06-22
Yes, I know it is a simple task, I have done it many times before. My main questions were about the partitions, and if I could format that partition while I am using Ubuntu. Also about Grub.

---

### Post by Bothered on 2007-06-22
You could try uninstalling ubuntu (and then if you still want to, reinstalling windows), although I'm not sure this is necessary if you just want to reinstall Windows from scratch.

I've uninstalled linux from a dual boot system before. I use the process:

1. Download mbrfix (search for it at download.com) and (in Windows) use it to fix the Windows master boot record. It runs in the Windows command line. Make sure you read the documentation before you use it.

2. If you don't already have it, download the ubuntu live CD and burn it. Then boot into ubuntu off the live disk. Run gparted (under System->Administration, but can be run from the command line) and use it to delete all linux partitions. You may need to unmount parititions first (sudo swapoff, sudo umount -a in the command line).

3. Use gparted to grow the windows partition to fill the rest of the available space on the drive.

4. Reboot (removing the live CD when prompted) and you'll have a Windows only system again.

EDIT: Point 3 only applies if you have one hard drive. If you have linux partitions on a drive other than that with Windows on, or if the Windows partition cannot be resized, leave the space blank and reformat it when back in Windows.

---

### Post by mikewhatever on 2007-06-22
> **TreeFinger said:**
> Yes, I know it is a simple task, I have done it many times before. My main questions were about the partitions, and if I could format that partition while I am using Ubuntu. Also about Grub.

Look at the pictures of the first guide. It shows the the whole process. If you want it typed, well, yes you can format the partition for Windows. 
> I know last time I formatted my entire hard drive I installed Ubuntu first and microsoft 2nd.
You seem to have done it before.

---

### Post by Bothered on 2007-06-23
Just a quick note to say that, before trying any of the steps in my previous post, it goes without saying that you should take precautions such as backing up data etc.

(This is directed at other users who may read it, rather than those that have posted here).

---

