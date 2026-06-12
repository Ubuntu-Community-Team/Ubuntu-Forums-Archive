---
title: "Installing 'Ubuntu Studio' on external USB 1TB drive"
date: 2013-01-02
forum: General Help
---

### Post by Silvernail on 2013-01-02
I know how to change the default boot drive. How do I change the default data drive.

What I would like to do is:
Install 'Ubuntu Studio' on an external USB hard drive. That way I can take it with me when I visit friends. And any work we do is saved to the default data files on the default data drive ( external USB drive ) and not to the computer drive.

Is there a How To on the data part or will the external drive automatically become the storage drive for all configurations and data?

---

### Post by oldfred on 2013-01-02
If you have /home on the external then data is saved in /home. Or you an have NTFS data partitions, but have to explicitly mount and save data to that partition(s).

You have to use Something Else or manual install to get the option on where to install the grub2 boot loader. png in last link shows the combo box. That is alternative installer but gui version is almost identical.

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

