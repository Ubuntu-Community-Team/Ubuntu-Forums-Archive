---
title: "Re-installation Help"
date: 2013-02-25
forum: General Help
---

### Post by TheBeezKneez on 2013-02-25
I would like to start off by saying that I am new to Ubuntu and forums as well. Lets get on with the problem now. I am on my old desktop, possibly about 7-8 years. It has 2 hard drives on it. 1 hard drive has Windows XP Professional installed on it and the 2nd hard drive is empty. So I decided to install Ubuntu 12.04 LTS on it and after having some graphic driver troubles I booted back into Windows and completely formatted the drive so that I could re-install Ubuntu on it. But, now when I try to boot from the Ubuntu CD, it hangs on the purple screen that says "Ubuntu" and never progresses. Most of the time it eventually changes to a black screen that mentions something along the lines of "Unable to handle kernel paging request..." Can someone please help me solve this problem? I would be very grateful. Thanks in advance.

---

### Post by oldfred on 2013-02-26
Welcome to the forums.

Linux does not recognize NTFS partitions for installing, so you cannot format a drive with Windows for Ubuntu. But it should give the option to overwrite.

Is system so old that it does not support PAE? If so you may need Lubuntu or Xubuntu. How much RAM do you have.
       [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

       [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

