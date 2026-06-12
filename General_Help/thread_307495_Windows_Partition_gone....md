---
title: "Windows Partition gone..."
date: 2006-11-26
forum: General Help
---

### Post by Chrono86 on 2006-11-26
Hey guys~
When I installed Ubuntu 6.10 on this computer I already had an NTFS partition with Windows XP installed. The NTFS partition didn't take up my whole hard drive so I used the free space to install Ubuntu on it. However after installing Ubuntu Windows didn't show up in the GRUB bootloader. The windows partition DID show up on my desktop though so I wasn't too worried. I then followed [this]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs") guide to allow write access to it and suddenly the partition no longer is mounted...it doesn't show up at all...so my 2 questions are how can I see it again and how would I make it bootable?
Thanks
Adam

---

### Post by Chrono86 on 2006-11-26
I don't like to bump threads, but this post got pushed back to page 4 in a matter of 3 hours...can anybody please help?

---

### Post by taurus on 2006-11-26
You need to look in /boot/grub/menu.lst to see if there is an entry for your XP, usually at the end of that file!

```
sudo cat /boot/grub/menu.lst
```

---

### Post by Chrono86 on 2006-11-26
Nope...just the 3 entries for ubuntu, recovery mode, and memtest...

Running fdisk -l does show my ntfs partition though, as hda5, if that helps.

---

### Post by taurus on 2006-11-26
Were you able to boot Windows before you started playing with the ntfs-3g thing?

Otherwise, what is the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Chrono86 on 2006-11-26
No, Windows never has shown up in GRUB since I installed Ubuntu, but the drive was always mounted on the desktop when Ubuntu booted, and all of its contents including the windows folder were in there.

As I said, fdisk -l does show my ntfs partition as /dev/hda5

---

### Post by taurus on 2006-11-26
Do you get a GRUb menu when you turn on your computer right?  Try to add this entry into your /boot/grub/menu.lst for your XP...

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.bak <-- make a backup copy just in case...
gksudo gedit /boot/grub/menu.lst
```
Scroll all the way down to the bottom of the file and add these lines in there!

```

title  Windows XP, eh!
root (hd0,4)
savedefault
makeactive
chainloader +1

```
Save it and reboot.  Now, you should see an entry for your Windows XP.  Use the down arrow to move to it if you want to boot it!

---

### Post by Chrono86 on 2006-11-27
It gives me an error 12, invalid device request when I choose the windows partition in GRUB. But now looking at fdisk's output I notice something funny:

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1              66       25008   200354647+  83  Linux
/dev/hda2           25009       36482    92164905    f  W95 Ext'd (LBA)
/dev/hda3               1          65      522081   82  Linux swap / Solaris
/dev/hda5           25009       36482    92164873+   7  HPFS/NTFS

Notice /dev/hda2. I also had a fat32 partition on here before I installed Ubuntu...and it appears to start and end on the same (cylinders? I think those are called) as /dev/hda5...is that supposed to be like that?

---

### Post by taurus on 2006-11-27
/dev/hda2 is called extended partition and under it, you can create some logical partitions and the first logical is known as /dev/hda5.  Therefore, you have your XP in the first logical partition of the first harddrive.  Both /dev/hda1, /, and /dev/hda3, swap, are your primary partitions.

Try changing the value in "root (hd0,4)" to "root (hd0,3)" or some other number until you get XP to boot...

---

### Post by Dragen on 2006-11-27
Don't worry!  Based on everything you have posted, everything is acting like it should.  When you installed Ubuntu, it installed GRUB and wiped your MBR so you use GRUB to boot now.  When this happened, GRUB didn't setup your boot menu.lst file correctly to allow you to select Windows from the menu.

your /dev/hda2 device is an EXTENDED partition, which means, based on what I can see... /dev/hda5 is the logical drive.  (This is normal.. Extend partition, and the logical drives are "children" of your extended device)

So try this:

sudo mkdir /mnt/windows

sudo mount -v -t ntfs /dev/hda5 /mnt/windows

It should mount successfully, and now try looking at it and see if you see the windows directory structure:

sudo ls /mnt/windows

If you see everything in there, then your windows partition is definitely THERE and not deleted.  Then it's just a matter of modifying your '/boot/grub/menu.lst' file correctly:

Try making this line:

root (hd0,2)

And try booting in to it.  Let us know how it goes!!!!

---

### Post by Chrono86 on 2006-11-27
> **Dragen said:**
> Don't worry!  Based on everything you have posted, everything is acting like it should.  When you installed Ubuntu, it installed GRUB and wiped your MBR so you use GRUB to boot now.  When this happened, GRUB didn't setup your boot menu.lst file correctly to allow you to select Windows from the menu.

your /dev/hda2 device is an EXTENDED partition, which means, based on what I can see... /dev/hda5 is the logical drive.  (This is normal.. Extend partition, and the logical drives are "children" of your extended device)

So try this:

sudo mkdir /mnt/windows

sudo mount -v -t ntfs /dev/hda5 /mnt/windows

It should mount successfully, and now try looking at it and see if you see the windows directory structure:

sudo ls /mnt/windows

If you see everything in there, then your windows partition is definitely THERE and not deleted.  Then it's just a matter of modifying your '/boot/grub/menu.lst' file correctly:

Try making this line:

root (hd0,2)

And try booting in to it.  Let us know how it goes!!!!

Well...I followed all of that.

The windows partition correctly mounted and I was able to see the directory structure which looked all in place.

So I then edited the grub line I had placed for windows there before and changed the hd0,5 to hd0,2.

Now when I select it in GRUB I get:

> Error 13: Invalid or Unsupported Executable Format

Now what's going on?

---

### Post by Dragen on 2006-11-28
Try doing  hd0,1  or hd0,0  or  hd0,3

It has to be one of them lol.  Trying them wont hurt anything, you just get an error you try to boot to a partition that isn't configured to boot.

As an example, this is how my 'sudo fdisk -l' looks:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3671    29487276   83  Linux
/dev/sda2            3672        3830     1277167+   5  Extended
/dev/sda3            3831        8929    40957717+  83  Linux
/dev/sda4   *        8930       14594    45496320    7  HPFS/NTFS
/dev/sda5            3672        3830     1277136   82  Linux swap / Solaris


And here is my menu.lst Windows entry:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista RC2
root		(hd0,3)
savedefault
makeactive
chainloader	+1


I'm glad to hear that your mount worked successfully.  (I also suggest putting the entry for it in your 'fstab' file so it automatically mounts during startup, by going to 'sudo gedit /etc/fstab':

/dev/hda5	/mnt/windows	ntfs-3g    defaults,locale=en_US.utf8   0    0

If you intend on using the above line in your fstab, make sure you download the 'ntfs-3g' package.. easily installed by 'sudo apt-get install ntfs-3g'.  it's a Writeable NTFS driver, and I have used it successfully. 

Give that stuff a go, and let me know if changing those numbers did anything for you.  It should!!

---

