---
title: "GRUB Loading stage1.5. Error 17"
date: 2015-04-29
forum: General Help
---

### Post by anythinganyway on 2015-04-29
My laptop is running on Ubuntu, the only OS. I formatted my hard drive with fdisk. When I restart my machine, I got

GRUB Loading stage1.5. 

GRUB loading, please wait...
Error 17

I searched the forum for solutions, but I cannot even open a terminal. What can I do now?[h=1][/h]

---

### Post by oldfred on 2015-04-29
That error is from grub legacy, which I have not dealt with since 9.10 or there abouts. Grub2 has been the standard since 2009. A few kept it and it may still be in the repository of some of the current versions.

What version of Ubuntu are you running? If not a current version then repositories are closed and you need to reinstall a current version. If current Ubuntu better to upgrade to current grub2.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by grahammechanical on 2015-04-29
> I formatted my hard drive with fdisk.

That action removed all files from the hard disk including Ubuntu but you still have Grub installed into the MBR of the disk and it cannot find its configuration files because the format removed them. What do you want to do now? Reinstall Ubuntu?

Regards.

---

### Post by anythinganyway on 2015-04-29
I am not completely sure which Ubuntu version I am running. I have not used the laptop for some time. But I guess the Ubuntu version is 10.04 or later, as I have installed a LTS version.

And yes, I have backed up the data and want to reinstall a newer version of Ubuntu.

---

### Post by oldfred on 2015-04-30
You then need to download ISO and use an installer to put it on a DVD or flash drive.
Will your system boot flash drives?
How much RAM and what video card? 
If older you may not be able to run full Ubuntu with Unity as it needs a somewhat newer system, but more RAM and better video card/chip.
Older systems then work better with Lubuntu or Xubuntu.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

---

