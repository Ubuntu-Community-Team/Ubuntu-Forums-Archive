---
title: "Ubuntu install shafts Windows (please help!)"
date: 2007-05-05
forum: General Help
---

### Post by floke on 2007-05-05
Dear all,

This afternoon I installed Ubuntu and Windows no longer boots.
When formatting in GParted the NTFS partition was resized but then GParted mounted the drive and then chucked an error saying it couldn't check it for errors (since it was mounted!). Since I had already defragged it and checked it for errors, and since Gparted had partitioned it before reaching the error, I continued with the install - only now Windows won't boot at all. Its still there - is being picked up in the sudo fdisk -l, and is mounted in the fstab - but just won't start up :(  (not my machine I installed it on - oops!).

The output if sudo fdisk -l is

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        4737    17567077+  83  Linux
/dev/hda3            4738        4864     1020127+   5  Extended
/dev/hda5            4738        4864     1020096   82  Linux swap / Solaris

The fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=95cbb696-d51b-45eb-aa87-e5e927fc09e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0C7CE3107CE2F2FE /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=6e248cce-ec57-460f-ba39-d9cea9ae58e2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And the stanza in the menu.lst is all fine - look...


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Any ideas??

---

### Post by JohnPhys on 2007-05-05
Can you be more specific about what happens when you try to boot windows?  I ran in to a similar issue with Vista last weekend and was able to recover, but I don't want to give bad advice :)

---

### Post by floke on 2007-05-05
Ok,

What happens is it just says 'starting up...' and that's it - just hangs there.
Here's what happened during the install:

I resized the XP partition with GParted - it resized, mounted the drive, and then errored about being unable to check the drives for errors (presumably since the drive was mounted). Since I had already checked the drive for errors I carried on - formatted the new space as ext3 stc. and installed Ubuntu merrily.

Now XP won't start up at all. I've done this like 20+ times with no problems at all. The first time I do it on someone else's PC it all goes pear shaped. 

Please help (and I really need this sorted by tomorrow else I think the person will reformat with XP again and ditch ubuntu) (bad news!).

---

### Post by floke on 2007-05-05
BTW: The boot flag for XP is set ok - just checked in the LiveCD.

anyone?

---

### Post by floke on 2007-05-05
anyone...?
help - I really need this mystery solved !

---

### Post by floke on 2007-05-05
nothing at all eh??

---

### Post by floke on 2007-05-05
:(

---

### Post by floke on 2007-05-05
Just Another bump

---

### Post by JohnPhys on 2007-05-05
Please try to be a little more patient, people are reading :)

At what point does the "Starting Up" occur?  Can you hit F8 immediately after selecting windows in GRUB to get to the menu to select "Safe Mode" for Windows?

---

### Post by floke on 2007-05-06
Sorry - just very annoyed *I think the people reading are me cgecking the thread!)
No - it's just the grub 'starting up' message...

Any ideas??

---

### Post by confused57 on 2007-05-06
You could try "rootnoverify" instead of "root":
```
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

and possibly remove the "savedefault" line.

What you can try is at the boot grub menu, highlight your Window's entry, press "e", then change the line with root to "rootnoverify (hd0,0)", without the quotes, then press "b" to boot...this is temporary, but can be made permanent if it works.

---

### Post by floke on 2007-05-06
Ok I'll try that and get back in about an hour or so (have got to go pick the PC up first)

Cheers

---

### Post by floke on 2007-05-06
Ok - this doesn't work - but I tried sudo fsck /dev/hda1 on the NTFS partition from the LiveCD and got an error 2 - fsck.ntfs not found

This looks like the core problem - any idea how to solve it?

---

### Post by JohnPhys on 2007-05-06
can you boot to linux from the hard drive (not live cd)?

If the error is limited to the ntfs partition, the linux stuff on the drive should work just fine.

IF AND ONLY IF THIS IS THE CASE (meaning you can boot to linux without the livecd, but not windows), you may want to install the package ntfsprogs (it's in universe, I think) and run

```
sudo ntfsfix /dev/hda1
```

If you have linux installed on the drive but cannot boot it, then there are other issues.

---

### Post by floke on 2007-05-06
Thanks for the help - I eventually fixed it by reformatting the whole drive with the xp rescue disk, and reinstalling everything. Crude and boring - but effective. Everything fine now.

Sorry for the impatience, but it wasn't my machine :popcorn: 

The world now has one more ubuntu user.

---

