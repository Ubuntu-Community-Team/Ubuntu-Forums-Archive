---
title: "Cant create LiveUSB"
date: 2016-01-16
forum: General Help
---

### Post by WinterMadness on 2016-01-16
I'm trying to make a LiveUSB for Manjaro. I understand that UNetBootin is not good for Manjaro.

Unfortunately the only software that seems to exist anymore is Unetbootin. I see references to all sorts of software that USED to exist on Ubuntu but I cant seem to find in the repos.

So I try this command: sudo dd bs=4M if=/home/joe/Downloads/manjaro-kde-15.12-x86_64.iso of=/dev/sdc

it outputs:

464+0 records in
464+0 records out
1946157056 bytes (1.9 GB) copied, 0.625726 s, 3.1 GB/s


and there is nothing on my usb drive at all still. The USB is formatted to fat32

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          32 62521343 62521312 29.8G  c W95 FAT32 (LBA)

---

### Post by howefield on 2016-01-16
Are you writing to the correct device ?

Which is it.. sdb or sdc ?

---

### Post by QDR06VV9 on 2016-01-16
> **WinterMadness said:**
> I'm trying to make a LiveUSB for Manjaro. I understand that UNetBootin is not good for Manjaro.

Unfortunately the only software that seems to exist anymore is Unetbootin. I see references to all sorts of software that USED to exist on Ubuntu but I cant seem to find in the repos.

So I try this command: sudo dd bs=4M if=/home/joe/Downloads/manjaro-kde-15.12-x86_64.iso of=/dev/sdc

it outputs:

464+0 records in
464+0 records out
1946157056 bytes (1.9 GB) copied, 0.625726 s, 3.1 GB/s


and there is nothing on my usb drive at all still. The USB is formatted to fat32

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          32 62521343 62521312 29.8G  c W95 FAT32 (LBA)

I use mutisystem and works good..
[http://www.unixmen.com/create-multiboot-usb-ubuntu-using-multisystem/](http://www.unixmen.com/create-multiboot-usb-ubuntu-using-multisystem/)

```
inxi -b
System:    Host: Arch Kernel: 4.1.15-1-MANJARO x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: ManjaroLinux 15.12 Capella
Machine:   System: LENOVO product: 1068AJU v: Lenovo B570
           Mobo: LENOVO model: Emerald Lake v: FAB1
           Bios: LENOVO v: 44CN43WW date: 10/27/2011
CPU:       Dual core Intel Pentium B950 (-MCP-) speed/max: 899/2100 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.17.4 driver: intel
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 11.1.0
Network:   Card-1: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8168
Drives:    HDD Total Size: 160.0GB (23.0% used)
Info:      Processes: 148 Uptime: 3:51 Memory: 763.5/3870.5MB
           Client: Shell (bash) inxi: 2.2.32 



```
You will also need xterm installed to run the script.
Pretty straight forward..
Regards

---

### Post by WinterMadness on 2016-01-16
[https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File#Using_the_Terminal](https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File#Using_the_Terminal)

dd bs=4M if=/path/to/manjaro.iso of=/dev/sd[drive letter]


Device Boot Start End Sectors Size **_Id_** Type
/dev/sdb1 32 62521343 62521312 29.8G **_c_** W95 FAT32 (LBA) 

so i used c

---

### Post by Dennis N on 2016-01-16
I suggest the method from the wiki linked in post #4 if you have no existing Manjaro system. It is what I used the first time installing Manjaro. But, once getting Manjaro installed, I started using Suse Studio Imagewriter which is in the Manjaro repository and it has not failed yet - even making several Ubuntu and Fedora installation media on USB.

---

### Post by howefield on 2016-01-16
With the flash drive connected, what does the following command return ?

```
lsblk
```

---

### Post by dragonfly41 on 2016-01-16
Perhaps this might work for you [http://www.pclinuxos.com/](http://www.pclinuxos.com/)

---

### Post by WinterMadness on 2016-01-16
> **howefield said:**
> With the flash drive connected, what does the following command return ?

```
lsblk
```

ive since formatted to ext4. 

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   256M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 461.5G  0 part /
&#9492;&#9472;sda3   8:3    0     4G  0 part [SWAP]
sdb      8:16   1  29.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1  29.8G  0 part /media/joe/d481035e-2177-4621-ae7a-ea58ee9ae871
sr0     11:0    1  1024M  0 rom

---

### Post by howefield on 2016-01-16
You can remove the usb stick and run the command again to make sure you have the correct device, but seems to me you should be using /dev/sdb

---

### Post by Dennis N on 2016-01-16
> **WinterMadness said:**
> 
Device Boot Start End Sectors Size **_Id_** Type
/dev/sdb1 32 62521343 62521312 29.8G **_c_** W95 FAT32 (LBA) 

so i used c

I inserted a flash drive, used fdisk -l, and got this:

```
Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1        2048 15147007 15144960  7.2G  b W95 FAT32

```
The correct device in this case is **/dev/sdd**

The letter 'b' in the output (under ID) identifies the partition type. 

b = FAT32
c = FAT32, LBA mapped

---

### Post by WinterMadness on 2016-01-16
Ok, so since I've been using so many programs and reformatting the usb drive so often, at some point an error occurred. Now fdisk -l looks like

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *        0  3801087  3801088  1.8G  0 Empty
/dev/sdb2        2048 62521343 62519296 29.8G ef EFI (FAT-12/16/32)

when I use gparted I get bizarre error messages.


How do I make it go back to normal? What even happened here? A usb drive is a usb drive. How is it acting like this?

Im starting to feel like its not possible to boot a manjaro live usb made in ubuntu...

---

### Post by WinterMadness on 2016-01-16
when trying to format /dev/sdb2/   (It used to be sdb1 and there is NOTHING else in the gparted list for devices)

Formatting to ext4:

"Partition(s) 1 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because they are in use. as a result the old partitions will remain in us. you should reboot now before making further changes"

---

### Post by Dennis N on 2016-01-16
> **WinterMadness said:**
> Ok, so since I've been using so many programs and reformatting the usb drive so often, at some point an error occurred. Now fdisk -l looks like

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *        0  3801087  3801088  1.8G  0 Empty
/dev/sdb2        2048 62521343 62519296 29.8G ef EFI (FAT-12/16/32)

when I use gparted I get bizarre error messages.


How do I make it go back to normal? What even happened here? A usb drive is a usb drive. How is it acting like this?

Im starting to feel like its not possible to boot a manjaro live usb made in ubuntu...

Well the direct write method (dd) doesn't write as files, it writes blocks of bits. So how you format it is not important. Just go ahead and set up and run the dd command, being very careful not to designate you hard disk as a target and destroy the contents. That is why it is dangerous if you are careless. Later, tools like Suse Studio Imagewriter (post #5) will protect your hard disk by only allowing writing to flash drives.

It was important to success, as I recall, to leave bs=4M. Other examples elsewhere may suggest different block sizes.

---

### Post by sudodus on 2016-01-16
Try ***mkusb*** :-) It wraps security around ***dd***, helps you avoid mistakes (for example that you overwrite a drive with valuable data). It is very reliable, but assumes that the iso file is a ***hybrid iso file*** (which is also the case with the plain ***dd*** method). The dd method is recommended at the Manjaro web site, so we can be rather sure that it is a hybrid iso file.

If you are running Ubuntu or a distro or re-spin based on Ubuntu, you can install mkusb from its PPA

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb

```

See this link for more details: [mkusb](https://help.ubuntu.com/community/mkusb)

You can install mkusb in other linux distros via the following link

[mkusb/gui#from_phillw.net](https://help.ubuntu.com/community/mkusb/gui#from_phillw.net)

If you are running Windows, you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

-o-

But there might be another problem. Please check with ***md5sum*** (or some other checksum) that the iso file was downloaded correctly!

---

### Post by QDR06VV9 on 2016-01-16
@sudodus <snip bad information> by poster edited by poster
It was GhostBSD that would not work with mkusb..Had to make that Clear.
At least I could not get one that would even boot off the USB..
So far the multisystem, and DennisN's suggestion image-writer(in the Arch repos AUR) have been the only tool that worked for me.. 
Kind Regards

---

### Post by sudodus on 2016-01-16
@runrickus,

Thanks for the heads up!

Some time ago, I used mkusb to make working pendrives for Arch, and in an Arch system without a graphical desktop environment I used mkusb-nox (no X) to create other USB boot drives. But this was more than a year ago with the kernel 3.16.1-1-ARCH x86_64 installed from

**archlinux-2014.09.03-dual.iso**

-o-

I will check what is the problem with mkusb for newer versions of Arch, and I can check it for Manjaro too, because I want mkusb to work :-P

-o-

I expect that ***mkusb should be able to create live-only pendrives of most linux distros*** (but not persistent live pendrives or Arch, Manjaro, Mageia and some other distros with different boot systems compared to Ubuntu and Debian). ***Edit:*** And I was not disappointed, it works as described in post #18.

---

### Post by QDR06VV9 on 2016-01-16
> **sudodus said:**
> @runrickus,

Thanks for the heads up!

Some time ago, I used mkusb to make working pendrives for Arch, and in an Arch system without a graphical desktop environment I used mkusb-nox (no X) to create other USB boot drives. But this was more than a year ago with the kernel 3.16.1-1-ARCH x86_64 installed from

**archlinux-2014.09.03-dual.iso**

-o-

I will check what is the problem with mkusb for newer versions of Arch, and I can check it for Manjaro too, because I want to to work :-P

-o-

I expect that ***mkusb should be able to create live-only pendrives of most linux distros*** (but not persistent live pendrives or Arch, Manjaro, Mageia and some other distros with different boot systems compared to Ubuntu and Debian).
Nice! That would be great, it would be nice to see one tool for all, But(in a perfect world) 
> mkusb-nox (no X) 
I must confess, I did not try that method yet..

---

### Post by sudodus on 2016-01-16
Right now I grabbed Manjaro, **manjaro-xfce-15.12-x86_64.iso**, via torrent and flashed it into a USB pendrive with mkusb, and it booted fine in UEFI mode in a laptop and in BIOS mode in an old desktop computer :-)

***Edit:*** I grabbed Arch, **archlinux-2016.01.01-dual.iso**, via torrent and flashed it into a USB pendrive with mkusb, and it booted fine in UEFI mode in a laptop and in BIOS mode in an old desktop computer I could boot both kernels, 64-bit and 32-bit :-)

In other words, ***mkusb*** and ***dd*** *can make USB boot drives from current Manjaro and Arch iso files* by {flashing/cloning/copying/burning/restoring} :-)

---

