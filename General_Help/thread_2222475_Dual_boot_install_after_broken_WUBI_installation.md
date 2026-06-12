---
title: "Dual boot install after broken WUBI installation"
date: 2014-05-06
forum: General Help
---

### Post by lennart3 on 2014-05-06
Need advice on how to make a HDD install after a broken WUBI install..

I did a 12.04 Wubi install, alongside Win XP on my old HP/Compaq d530 desktop.
It was working, but very slow. Used it a little but it was no good for permanent use. So I decided to try Lubuntu 14.04, from a bootable CD (no install) in order to find out if it was faster (should be?...).

That operation was not very succesfull...After a while, soon after startup screen of Lubuntu from CD, the computer hang and I had to press the off switch, because the keyboard stopped responding.

After reboot I got the "missing hal.dll" message and neither XP nor my existing(?) 12.04 install was working anymore. After some serious hacking and with the aid of XP installation CD (and DOS edit) I found that hal.dll was there, but the boot.ini was messed up. It took a long time - but I somehow edited boot.ini so that XP can start, but nothing else. So it seems that the Wubi installation (and/or GRUB/boot.ini) is now corrupted ?

So - my questions : What to do next, I have to keep XP because I need one (1)
licenced program (with a hidden license ID somewhere on the HDD)- it does not work with WINE.

I would like to make a "real" install of 14.04 (not Lubuntu, because of the mishap when running from CD). 14.04 works very well on my Laptop so my guess is that it will run OK (but slower) on the Dell desktop as well.

But I might even consider installing 12.04, because I know for sure that it was working on the desktop computer with the WUBI installation.

The questions:

Is it safe to go ahead and remove the wubi installation completely (from within XP) and make a real HDD install of 14.04 and expect a working 14.04 on the HDD after that mishap with Lubuntu, leaving WIN XP untouched? Is there something I need to do before doing so ? Or is it better to keep to 12.04, known to work OK on the desktop computer?

Will such an installation make a totally new GRUB or will I experience new trouble - like errors in GRUB and/or new "missing hal.dll" issues ?

(It took me quite a time to get XP back after the boot.ini error and it was more luck than experience involved in that recovery...).

Thankful for any comments and suggestions !

---

### Post by Mark Phelps on 2014-05-06
Lubuntu will appear more responsive on lot resource machines because its User Interface (UI) is more basic than the Unity one used in Ubuntu -- which is wy we generally recommend it for lower resource/older machines.  But ... it should not HANG.

Also, the missing dll message tends to indicate (presuming that the file was not actually removed) a corrupted Windows filesystem and, presuming you did nothing to cause this (like, writing to the Windows filesystem from inside Linux), that, in turn, tends to indicate a failing hard drive.

One way to see if the hard drive is failing is to run a partition Check on it.  If Windows is working, you can do that by right-clicking the partition (Windows calls it a "drive") and choosing the option to check and repair the filesystem.

If that is not available, you could also try downloading the ISO file of the Minitool Partition wizard Boot CD, burning a CD from that, booting from that -- and using the option to Check the partition.

If you do have a failing drive, not only will installing another OS probably fail, even if it works, it's eventually going to fail -- due to the hard drive.

---

### Post by lennart3 on 2014-05-07
Thanks for your reply,
I did check and repair of HDD in Win XP - but nothing wrong ... Any more suggestions ?

---

### Post by oldfred on 2014-05-07
Almost always the missing hal.dll issue is related to boot.ini. And wubi had to write the new entry for wubi into boot.ini and that normally works, but it sounds like in your case there was some issue. 

Installing to a separate partition should not give any issues, other than you need to shrink the NTFS XP partition and reboot it immediately so it can run chkdsk. Better to do that before install with gparted than as part of install. While many have reported no issues shrinking NTFS partitions during install, many others have had issues.

If you saved data that you still want in your wubi you can recover that from a liveDVD. Wubi is just one large file root.disk on your NTFS partition and it can be mounted, fsck if needed(like chkdsk but for Linux ext format) and data read from it. 

Always best to have a full backups of your Windows install. Any partition changes can cause issues. Most times it works, but it always seems like the one time we are in a hurry and skip backups is the time something wicked happens.

Installer has not changed a lot, not sure how much Lubuntu is different, but mostly in colors of screens. Process is very similar across versions and flavors.
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

### Post by stalkingwolf on 2014-05-07
once you have checked everything defrag at least 2 times before resizing the partition.

---

### Post by lennart3 on 2014-05-07
Thanks for all info.
I will read all info and act after that.
Meanwhile I found that the reason for the hang when trying Lubuntu is probably
caused by incompability with the Rage 128 Pro  Ultra GL graphics card in  the Dell D530. I tried to run Lubuntu from CD again and what happens is  that it can not find a proper screen setting by default, it looks like  2:5 instead
of 4:3 = most of the info is outside the visible screen area. It is  impossible to read anything on screen - most info is outside viewing  area. I think that the graphic card does not like that either.  BTW I  remember some issues with that card as incompability with Google Earth  in Windows. Not the best graphic card in the world....
I will report back ASAP.

---

