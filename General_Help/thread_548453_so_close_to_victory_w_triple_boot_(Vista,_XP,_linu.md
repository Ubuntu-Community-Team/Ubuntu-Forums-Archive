---
title: "so close to victory w/ triple boot (Vista, XP, linux)"
date: 2007-09-11
forum: General Help
---

### Post by ericnord on 2007-09-11
Hey everyone,

I've spent three days trying to get Vista, XP and Suse all running. I can get each to run individually and now have Vista and Suse running via GRUB, but I lost XP. Sorry for the long message, but I've read everything I could first and still no luck. It is just some small item I'm sure. Using Suse becaue my abit ip35 pro has the jmicron issue that Ubuntu has issues w/.

Setup:
sda
hd0,0 - Vista primary partition NTFS
hd0,1 - XP primary partition NTFS
hd0,2 - Suse primary partition EXT2
hd0,3 - NTFS space for data

sdb
hd1,0 - primary partition Suse swap
hd1,1 - primary partition XP swap
hd1,2 - primary partition Vista swap
hd1,3 - NTFS for data

sdc
hd2,0 - NTFS primary for data

Steps I followed:
1. Start w/ three fresh drives and empty MBR, GRUB, etc.
2. Install XP to second partition on first HD (hd0,1). I did this because I read that Suse cannot move a Vista partition so it would be best to leave Vista on 1st partition. I also heard that XP should be installed first so Vista bootloader auto dual boots XP. All of this = me installin XP first, but on second partition
3. remove all media and boot to XP and do this a couple times to make sure MBR is good and XP loads as it should
4. Boot to Vista CD and install it to first partition of first HD (hd0,0). Remove all media and make sure it boots fine on its own
5. Here I noticed that I was not getting the dual boot from Vista boot loader. Vista would boot straight off w/ out recognizing any other OS.
6. Install Suse to first HD third partition hd0,2. Also install Grub to this partition and add XP as hd0,1 w/ rootnoverify and chainloader +1. Same w/ Vista except hd0,0
7. Reboot Suse and except Suse at Grub loader....Suse works fine.
8. Vista loads fine from Grub loader, but once I select it I get a bunch of text for a second that I don't have time to read, but I can catch GDLR outputted to the screen.
9. Select XP from Grub loader and it stops on screen w/ only text saying, rootnoverify (hd0,1) chainloader +1

So, I can boot into Suse and Vista just fine. I've gone into my menu.lst file and it is all correct, identical to Vista except w/ the proper partition. I've tried using Super Grub boot CD to boot the hd0,1 partition, but it just sits there w/ the boot command. I've verified everything w/ fdisk -l, I've tried to make the XP partition active first in both menu.lst and Super Grub, etc. XP will no longer boot...

One weird behavior that might offer some clue is when I now (system in state described above) insert the XP boot CD it says it cannot continue because no HD are connected. This is weird because if I take the CD out and boot to grub Vista and Suse boot fine.

The only thing I can think is that XP wrote the MBR to the second partition hd0,1. When I installed Vista it wrote MBR to first partition so that could explain the reason Vista didn't know XP was there. But I thought Grub on the booting partition hd0,2 could be told to boot any partition regardless of what the partitions MBR says.

Any ideas?

---

### Post by confused57 on 2007-09-11
Maybe you need to hide the Vista partition from XP in your grub entry:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)

---

### Post by ericnord on 2007-09-11
Thanks for the link. Tried it but it didn't change anything. I'm thinking Vista just overwrote some XP MBR stuff. Gonna wipe all drives and try again.

---

### Post by nwadams on 2007-09-11
ok, install xp, then vista, then linux...because for me i had grub and then when i clicked windows...it sent me to the vista boot loader...so essentially i had 2 boot loaders

---

### Post by ZMEZman on 2007-09-19
Yes, you will have to have two boot loaders. I have a quad boot system, Windows XP Home, XP Pro, Vista and Ubuntu....

My system always boots to ubuntu or Vista/Longhorn I boot to this and I get all three other Operating Systems to chose from...XP Home, XP Pro, and Vista...Its a dual Boot/ triple boot...lol

It also depends on what Bios you're running.

---

### Post by jeremy12 on 2008-05-01
> **ZMEZman said:**
> Yes, you will have to have two boot loaders. I have a quad boot system, Windows XP Home, XP Pro, Vista and Ubuntu....

No...

I stumbled apon this thread while looking for information about grub hiding partitions. i know its a bit old but it will most likely help someone.

I am currently working on a System that boots into Vista, Xp, 2000, and Ubuntu (Grub boot loader) all with one menu, its really simple just download a CD bootable copy of Gparted ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) then do this:

1. boot to Gparted make Vista partition
2. install vista
3. boot to gparted hide vistas partition and make a XP partition
4. install xp...
3. boot to gparted hide xp's partition and make a 2000 partition
4. install 2000...
5. boot to you linux installer tell it to automatically partition the remaining space, by making itself 2 partitions inside a extended partition, you can latter change the size of the ext2 partition with gparted to have a "storage" partition visible in all OS's
6. edit your grubs menu.lst to hide partitions not being used and unhide the partition being booted to
7. enjoy!

---

