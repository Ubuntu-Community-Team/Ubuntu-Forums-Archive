---
title: "Micro SD card only mounts RO"
date: 2015-06-04
forum: General Help
---

### Post by miatawnt2b on 2015-06-04
I am hoping someone here can help me troubleshoot this. I have an Acer laptop running a fresh 15.04 Ubuntu 64bit. I have installed the latest 4.1rc6 kernel, but this problem also occurs with the stock kernel.

The laptop has a microSD slot (one of the tiny ones like phones/tablets typically have)

Inserting the microSD,  Ubuntu will mount it automatically, but it will only mount read only. I tried to also add it to /etc/fstab to get it to mount RW automatically, but it still is only read only after boot.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/mmcblk0p5 during installation
UUID=9e36d6d7-061d-479d-b768-1c8e855a7d4b /               ext4    errors=remount
-ro 0       1
# /boot was on /dev/mmcblk0p4 during installation
UUID=a74a4d7b-a1c7-44f6-a73b-e4fa7a3cf620 /boot           ext4    defaults      
  0       2
# /boot/efi was on /dev/mmcblk0p1 during installation
UUID=2680-97FB  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/mmcblk0p3 during installation
UUID=8af40125-5b7d-4779-9e72-d2d297818ac9 none            swap    sw            
  0       0

UUID=A4A5-1F92 /mnt/sdcard	vfat	auto,exec,rw,async,user 0 0

```

If I pop out the card and put it into into a microSD to SD adapter and stick it in my other laptop (also running 15.04) I can mount the drive RW no problem. 

Would anyone please be able to help me get this working properly?
Thanks!
-J

---

### Post by DuckHook on 2015-06-04
Sounds like it may be a permissioning problem. Are you the exact same user ID on both laptops? Do:```
id
```on both machines to see if your user IDs are identical. If not, then the SD card will only *rw* on the machine it was created on and not on the other with a different user.

No point in mounting the card in *fstab* which is more for built in hdd and ssd. In fact, this could gum up your system when the card is not present, so best to delete the entry.

You can change the permissions on the card at the root directory to allow *rw* access to "others". This will make it universally read/writable to anyone. Remember to recurse any such permission changes to all subdirectories and files.

**Correction**

Did not read carefully enough. Your card SD is formatted vfat, which does not have permissions, so above cannot be true (unless you reformatted it in some ext format). Will have to think more on this one.

---

### Post by miatawnt2b on 2015-06-05
yep, I screwed around with permissions and formatting it ext4 on the other laptop then chmod 777 the mount point on the problem machine. No luck there, so I just stuck the card in a windows box and formatted fat32 to get to a known starting place. 

I have no idea what's going on with this thing. I am wondering if the sd controller driver is messed.

-J

---

### Post by miatawnt2b on 2015-06-08
Any Ideas?

---

### Post by miatawnt2b on 2015-06-21
bump

---

### Post by haplorrhine on 2015-06-21
Flash memory degrades with time, and algorithms in the controller are designed to preserve data integrity as the blocks go bad.  I've heard on these forums that, after a certain point, they will mount read-only.
Some people reprogram the controller.  You could check whether that company released the software they used to program it in the first place.

---

### Post by miatawnt2b on 2015-07-09
still no luck. I was hoping an upgrade to latest 4.1 kernel would help, it didn't. 
Could someone please help! the card works in windows, it also works in my other linux laptop when plugged into a microsd to SD adapter with the WP switch off. I think this proves the card is fine.
-J

---

### Post by halfnote52 on 2015-08-01
Having the same problem. BRAND NEW MicroSD SDXC card (64 gig) and it works BEAUTIFULLY under Windows.  I even repartitioned it using FDISK, cleaned it, and made a big FAT32 partition to see if Linux would play nicey-nice and NOTHING.

It SEES it, it READS it from the micro-sd slot in the lappy, but it will NOT let you write anything to it.  gparted won't let you touch it, and even in dmesg it says "new high speed SDXC card at address 0007 blah-blah-blah 64Gib (ro)   

Yup. READ-ONLY.

Remount rw does not work. wipefs won't touch it, dd will not wite even a sigle byte to it. All give the same error "read-only filesystem"

I was starting to think it's a driver/software issue, but it reads it fine and recognizes it fine, so I dunno about that. Could be a problem in the driver's write module? Older linux distros would mount ntfs as ro until you installed ntfs-3g.

It's a known good card. It's NOT an exfat problem because I reformatted it. I even tried NTFS once to see if the ntfs-3g module would maybe wanna take a swipe at it. 

Apparently there's something I'm missing, too.



Also, googling the issue results in a lot of people with standard-sized SD cards who didn't know about the lock switch. I can assure you this isn't the case here. It's a microSD, after all, and the slot doesn't require an adapter. It's already micro. ; )

---

### Post by halfnote52 on 2015-08-02
P.S. Aforementioned SDXC MicroSD works FINE in another laptop in Xubuntu 15.04 (on an Acer Aspire Switch 11.)    But does NOT work on an Acer Aspire Switch 10 (Same version of Xubuntu - Live system was MADE from the Swtich 11's hard drive clone).

Wondering if it's something to do with the BayTrail chipset in the Switch 10. (Again, back to the SDXC driver issue?)  OP said "Acer" but never mentioned a model. Could be worth comparing notes on chipsets.

---

