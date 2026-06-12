---
title: "cannot repair grub!"
date: 2007-02-03
forum: General Help
---

### Post by geodeath on 2007-02-03
Well, i know this have been covered, but no matter which solution i tried, i could not repair grub.

My problem is this:

When i first installed ubuntu, i installed it on SDA, where SDA1 is the linux partition and SDA3 (if i remember well) is the BOOT partition. There is an NTFS partition taking up the rest of the HD.

However this is not the only HD in the system. There is also HDA where everything is XP & NTFS. I decided to install grub onto the mbr of HDA, so there is always the bootloader when i power on my pc (i mean, so i dont have to select a boot device to go to linux, but just select it from a menu).

Yesterday a friend came needing assistance with his HD, and i popped it in the slave position, after HDA. After installing this second HD, i couldnt boot into windows or linux, grub gave me error 17. However, because i needed to boot into XP to fix his problem, i decided to repair my HDA mbr back to the winxp one and later to repair my grub so its installed onto the SDA hd.
I hope you are still with me.

Since then, i cannot install grub correctly. when i try to boot from SDA, it shows me the grub menu, but i cannot boot anything cause i am getting error 17 again.

I can provide info about the setup of the disks with fdisk if you want, just be patient, cause although i am enthousiastic about ubuntu and linux in general, i am not really experienced yet.

thanks a lot :D

---

### Post by bernied on 2007-02-03
It sounds like your situation is a bit complex because you have two types of HD installed (the sd* and the hd*). I suggest you get yourself a Super Grub Disk. You can read about it and find a link to download it [here](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) (and have a look around the rest of this site while you are there, it is a site dedicated to dual-booting and grub, and Herman is very knowledgeable). 

Remember that, as Linux is not Windows, grub is most definitely not Linux (it is an independent boot-loader that is almost an operating system in its own right). The point is, that grub sees disks differently to linux, so for example hda does not always map to hd0.

Learn about grub.

---

### Post by r4ik on 2007-02-03
If i fully understand you're post this should work.
Here is the link,

[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

if unsure ignore or wait for confirmation.


Restoring GRUB is quite simple in Ubuntu. Instead of going through all the "gain root access" and playing with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

### Post by geodeath on 2007-02-03
thanks for both the info & the solution to you both. Will try doing that tomorrow morning. Its bedtime :D

---

### Post by r4ik on 2007-02-03
I am NOT going to sing for you :)
Sleep tight.

---

### Post by geodeath on 2007-02-03
well, it doesnt matter. I have my ipod always by my side.

Although for some reason, it sounds interesting :-\"

---

### Post by geodeath on 2007-02-04
well, it seems that i cannot get past the partition stage, because i will not allow me to select my / and /boot without formatting them. I am talking about the 6.10 install cd here. Its kinda different. You cant just select mount points as the other tread says. You have to select the HD you want and in the next step you have to select mount points.

It doesnt allow me to continue if i dont have format ticked and i am not sure if its going to format the disks right away or not.

:(

---

### Post by mbradlcu on 2007-02-14
here's what worked for me... I tried the various suggestions
1)
run boot CD
mount /dev/sda1 /mnt  #where edgy was working and installed
chroot /mnt
grub-install /dev/sda
"nope, no device found, so this didnt' work

2)The re-install method didn't allow me to proceed with out reformatting /

so I tried:
run boot CD
sudo -s
grub
find /boot/grub/stage1
root (hd2,0)   #this points to sda,, but I noticed if I removed my pull out drive, find /boot.. showed it as hd1,0 humm?
setup (hd0)
"nope no joy, boot still presented me with error 15"

so after rebooting and being presented with the grub boot loader, I selected "e" and edited
root        (hd2,0)   #and changed it to
root        (hd0,0)

A little speculation here, I use the bios to point to the boot loader, I'm wondering if when I boot from CD grub sees it relative.. I'm guessing so as when I removed hdb, grub failed even though it didn't have any entries pointing to it,, nor did the fstab.

---

