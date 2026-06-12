---
title: "grub rescue, but no partitions are readable??"
date: 2015-10-14
forum: General Help
---

### Post by bcad on 2015-10-14
I have an Acer netbook with windows 7 that I have ubuntu and some other distros on (antivirus, gpart, lubunutu etc). Today, I accidentally clicked the windows recovery boot option in the list as its right next to windows 7. i simply exited but when it reboot to get back to the menu, it went directly to a black prompt called "grub rescue>"

I have done quite a few google and youtube searches, but I have a problem. ls'ing the partitions ALL result in an "unknown file system" result, so there is no way to set a patch to a /root for the "insmod normal" or set root/prefix step through fix's.

ls gives me the following:
(hd0), (hd0,msdos5),(hd0,msdos3),(hd0,msdos2),(hd0,msdos1)

ls'ing any of those all returns the same "unknown file system".

if i try the set root/path method and just try for each, everytime i get to the part to run "normal" it says unknown command or something like that, i dont have it in front of me i left it at work by accident.

but, now what? i dont have an external cd drive, nor windows cds to try a random repair mbr program from somewhere.

thanks all!

---

### Post by oldfred on 2015-10-14
On some systems just going into the Recovery, rewrites the partition table. And Windows tools do not correctly see Linux  partitions. If your Linux partition was sda5 or a logical partition it is now missing from partition table, but still exists on drive.

parted rescue or testdisk can often restore missing partition. 
Post this, just to confirm issue:
sudo parted -l

---

### Post by bcad on 2015-10-15
i cant, im not in any shell that i know of, just this "grub rescue>" prompt. there is no sudo, parted, help, ?, cd etc or any standard command other then ls and set as found in the tutorials that dont seem to cover when there is no listing from an ls command on any of the partitions it finds. i have no idea what partitions are what, i installed the system 4+ years ago.

---

### Post by oldfred on 2015-10-15
You need to use your Ubuntu live installer in live mode.
What version of Ubuntu are you using? 

Or download a new one.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by bcad on 2015-10-15
I got in with the live usb I originally installed it with.

sda1 ntfs Windows Recovery Environment 12.8gb
sda2 ntfs Windows 7 (loader) 106mb
sda3 ntfs unknown 82gb
free space 63.9gb
sda5 swap 1060mb

The unknown and free space bother me. Ubunutu was working fine before, now it seems to have self destructed?

Also found out that the Windows partition is in sleep mode and cannot be mounted unless i shut windows down (which i cant do because i cant boot into it obviously)... but after i tried a boot-repair program its now mountable and the windows data is all there, but it still wont boot and goes right to the rescue prompt. when mounted it is 82gb in size so it must be sda3.

---

### Post by bcad on 2015-10-15
fdisk shows me this:

1 hidden ntfs winre
2 hpfs/ntfs/exfat (* boot flag)
3 same as above
4 extended
5 linux swap

im assuming now that 4 was my ubuntu partition which is now blank, hence grub rescue ls cant find anything to latch too to boot. im also assuming that the data and ubuntu are still on that partition, but for some reason it doesnt recognize it anymore. how do i fix THAT without reinstalling ubuntu onto that partition and HOPING that will also fix the mbr somehow so i can get back to windows.... sacrificing my ubunutu data....

---

### Post by oldfred on 2015-10-15
If you leave Windows hibernated or with the Windows 8 or later fast start up on, grub will not boot that Windows. Grub only boots working Windows. You need to directly boot Windows. You may need a Windows repair CD or flash drive to run chkdsk on the Windows partition.

Many users with your issue, have used parted rescue or testdisk to restore the missing partition. It probably was sda5 and swap was sda6, but recreating the Linux partition as sda6 should not matter as grub uses UUID to boot partition.

If you run this to see sectors then you know the start and end sectors as it must be one or two sectors after start of extended partition and several sectors before the start of swap. 
       sudo parted /dev/sda unit s print


            Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)#

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by bcad on 2015-10-16
parted worked using the start/stop positions gparted live was able to find for the "unallocared" partition that was my ubuntu install, and mbr fixed itself upon reboot. thanks for finding the solution!

---

### Post by oldfred on 2015-10-16
Glad that worked.
Please change to solved, so others can find a solution.

---

