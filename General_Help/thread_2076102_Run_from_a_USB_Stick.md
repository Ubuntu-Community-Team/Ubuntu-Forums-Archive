---
title: "Run from a USB Stick?"
date: 2012-10-25
forum: General Help
---

### Post by jonburton on 2012-10-25
Hi,
 
New to Ubuntu so sorry if this is a basic question..... I believe it is possible to run a full Ubuntu 12.10 from a USB stick including installed apps and data - Please could someone let me know how to do this...... Or, I have Ubuntu installed with my apps on a laptop is there a way of "backing this up" to a live USB stick?
 
Cheers

---

### Post by pmlxuser on 2012-10-25
if you are running ubuntu on usb and you provided enough space for installation you can install on it and it will run ok, do you have enough space on your USB..am not sure about the second one..."backinh this up" to live usb..

---

### Post by jonburton on 2012-10-25
I was going to purchase a 64gb memory stick - How would I go about installing Ubuntu to this please?

---

### Post by NikTh on 2012-10-25
> **jonburton said:**
> I was going to purchase a 64gb memory stick - How would I go about installing Ubuntu to this please?


IMHO Ubuntu installation (and any OS) in a Usb stick would be a nerve war. Why ? 

Because usb is too slow compared to an HDD (even old IDE HDDs). 

I would suggest to create a Live-USB of Ubuntu with persistent space. Persistent space will allow you to save your configurations and because is running in the native USB filesystem (fat32) will behave better than ext4. 

You can create a presistent  space with Ubuntu's startup disk creator look here 2nd post.
[http://ubuntuforums.org/showthread.php?t=2041448](http://ubuntuforums.org/showthread.php?t=2041448)

or 

with [Universal USB installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) , look at 4th step in picture. 

This is just my opinion , cuz tested both in past and Live-USB behaves better and faster for me. 

Thanks

---

### Post by evilsoup on 2012-10-25
If you really want to run an OS off a USB memory stick for a serious length of time, you'd be better off using something like Puppy Linux, which is specifically designed for that.

---

### Post by oldfred on 2012-10-25
I do have a full install on a USB flash drive. And USB is slower than SATA, Flash is slower than a hard drive, but with settings similar to SSD to minimize writes and lots of RAM so once loaded programs stay available a flash install can be functional. Initial install is slow as that is all writes. I just use it for testing on my laptop as it does not have a second drive.

Some suggest the lighter weight versions like Lubuntu for flash drives as then you are loading smaller apps or a bit faster loading initially.
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

An install to flash drive is just like any install to a second drive. And you need to use manual install or Something else to get the choice on which MBR to install the grub2 boot loader.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Herman now uses Alternative (Text Based) installer. His older version was the gui and I followed that. Install process is the same whether text based or gui.

It does not have to be encrypted BIOS based system (you do not need LVM if not encrypted):
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)


Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Version does not really matter with installer:
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

### Post by NikTh on 2012-10-25
:)

[[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")'s answers always are just like to read  encyclopedia. 

Thanks for the links.

---

### Post by C.S.Cameron on 2012-10-25
It is possible to clone your laptop drive to an external drive, if the external drive is larger than the internal.
I do this with m wife's desktop so that she can boot the external drive from my laptop when we are traveling.

I use dd for this, read up on dd before trying it is a good tool for professionally wiping hard drives..

---

