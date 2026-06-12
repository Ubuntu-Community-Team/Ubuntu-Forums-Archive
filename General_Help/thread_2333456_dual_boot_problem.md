---
title: "dual boot problem"
date: 2016-08-10
forum: General Help
---

### Post by bekzod on 2016-08-10
Hi guys. I had a windows7  and ubuntu on my pc. I reinstalled windows 7 and now having problem to load in ubuntu . The first OS in boot manager was ubuntu probably thats why probably i deleted MBR . Tried to google but so far didn't find how to fix it. 
Please share your help guys. 
thank you

---

### Post by techyzen101 on 2016-08-10
Do you have the installer for the same ubuntu version your PC has?

---

### Post by grahammechanical on 2016-08-10
You will have to explain the steps you took in re-installing Windows 7. Right now, I am assuming that the new installation of Windows 7 over-wrote the installation of Ubuntu. It can happen. It is certainly possible to install Ubuntu in such a way that any other operating system will be erased. May be the re-installation of Windows 7 did that to Ubuntu.

You can open a Windows utility and examine the partitions of the hard drive to find out if Ubuntu is still installed. If Ubuntu is still installed you will need to re-install the Ubuntu boot loader (Grub), at the very least.

Regards

---

### Post by oldfred on 2016-08-10
Was Ubuntu in a logical partition?
This is the old Windows bug that is now happening with every BIOS update from Windows 7 to Windows 10.
Windows rewrites partition table on major updates/reinstalls. But it just forgets to include Linux extended partition(s).

You can use parted rescue or testdisk. Best to backup current partitions first as a few have not saved correct set of partitions from testdisk and could not get back to starting point.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

       Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors:
sudo parted /dev/sda unit s print 

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by bekzod on 2016-08-10
I re-formatted windows disk C from Ubuntu to NTFS  , then booted from windows disk and installed win 7 exactly on that partition. I am sure ubuntu partition  is not over-written because i tried to use some apps under windows and they still see linux partition, also after restart windows bootloader still ask me to chose to boot windows or ubuntu . I have no live cd of that OS I had on my pc , but i found disk with Knoppix-STD linux and Kubuntu . I am not sure can they help me .

---

### Post by oldfred on 2016-08-10
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bekzod on 2016-08-10
ok,  i solved this issue partially with boot-rescue-disk I downloaded iso then burned on flash drive and then from it restored grub . Now i see grub and only Ubuntu as option which i can boot (im writing from it now :). How to add existing  windows 7 into grub now ? 
thank you

---

### Post by oldfred on 2016-08-10
First try:
sudo update-grub

If not, post link to summary report from Boot-Repair.

---

### Post by bekzod on 2016-08-10
thank you "oldfred" ur advice fixed issue .

---

### Post by oldfred on 2016-08-11
Glad that worked.

Please change to solved, see info below in my signature.

---

