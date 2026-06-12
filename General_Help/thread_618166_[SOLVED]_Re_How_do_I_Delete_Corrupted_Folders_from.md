---
title: "[SOLVED] Re: How do I Delete Corrupted Folders from Usb Key?"
date: 2007-11-20
forum: General Help
---

### Post by Sef on 2007-11-20
Found the problem with moving my folders off the usb to the new computer.   On the USB there are some corrupted folders.   Unfortunately, they have photos.   Moved the good folders over, but how do I delete the bad folders.   The trash icon is grayed out, and when I try and manually move them to the trash can, they say access denied.

---

### Post by Rinzwind on 2007-11-20
Unless that's not an option: can't you format it?

---

### Post by Sef on 2007-11-22
Bump. Any idea?

---

### Post by Sef on 2007-11-28
bump.

---

### Post by Samhain13 on 2007-11-28
Just a theory:
Access denied means the the user trying to access the files has insufficient permissions, right? Why not try deleting the folders as Super User?

```

gksudo nautilus

```

Then navigate to the drive and delete the folders.

---

### Post by Sef on 2007-11-28
> Access denied means the the user trying to access the files has insufficient permissions, right? Why not try deleting the folders as Super User?

When I do that, it does not detect the usb or maybe I don't know how to navigate there.   No icon shows up when I go into nautilus.

Update:  I am able to get to the folder, but still have the same problem.

---

### Post by Sef on 2007-11-30
bump

---

### Post by -grubby on 2007-11-30
have you tried reformatting it?

---

### Post by Sef on 2007-12-02
How would I do that?

---

### Post by Sef on 2007-12-05
bump

---

### Post by Sef on 2007-12-08
bump

---

### Post by der_joachim on 2007-12-09
I am not a gnome user, but I happen to know that it is possible to open a konsole in konqueror with a single keystroke. The working directory is the working directory of konq, which in your case should be your USB stick. Maybe Nautilus has such an option as well?

A sudo rm -rf badfolder would do the trick, I guess, although your past from last week suggests otherwise. 

Does gparted detect your USB stick? That's how I managed to format a bad usb stick once. TBH, I used qtparted, but these are practically the same.

Good luck.

---

### Post by Sef on 2007-12-09
> Does gparted detect your USB stick? That's how I managed to format a bad usb stick once.

Yes, it does.   I will try with that again.

---

### Post by Sef on 2007-12-15
Bump. Any other ideas.  It says that is read only.

---

### Post by Sef on 2007-12-19
bump

---

### Post by FuturePilot on 2007-12-19
Not sure if this will work but you could try to fsck it. I'm assuming it's some variation of FAT.
Plug it in, wait for it to mount, then unmount it. We don't want it mounted while we do this.
Then
```
sudo fsck.vfat -a /dev/sdXY
```
Replace XY with whatever it happens to be. You can find out with 
```
fdisk -l
```
Then if it repaired anything you might be able to delete the folders.

---

### Post by Sef on 2007-12-19
Tried 
```
sudo fsck.vfat -a /dev/sdXY
```


This is what I get when I do it:

> dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sda1:Read-only file system


How can I make it read-write?

---

### Post by der_joachim on 2007-12-19
> **Sef said:**
> Tried 
```
sudo fsck.vfat -a /dev/sdXY
```

(...)

How can I make it read-write?
```

sudo mount -t vfat -o rw /dev/sdXY /media/yourmountpoint 

```

or something like that. The '-o rw' switch explicitly mounts the USB stick writable.  However, I think that something is very wrong with your USB stick and that a mere mount will not really work. Either that, or that stick has been locked or something. I have a USB stick which can be 'locked', so that nothing can be written to it. I assume that that is not the case with yours though.

---

### Post by Lostincyberspace on 2007-12-19
I ended booting into windows and reformatting it.

---

### Post by Sef on 2007-12-21
```
sudo mount -t vfat -o rw /dev/sdXY /media/yourmountpoint
```

So my mount point would be "/dev/sda1? or is it something else?  (/dev/sda1 is what I get when I do an fdisk -l check.)

---

### Post by der_joachim on 2007-12-21
Hmmmm... I do not know your hardware and if you have SATA or SCSI disks, these will probably get the device numbers sd* as well. Could you post the output of fdisk -l please? If you have good ol' PATA (IDE) disks, and your fdisk -l gives you a/dev/sda1, you probably have the right device anyhow. A nice way to doublecheck is simply viewing your mounted partitions. It would probably look like this:
```

/dev/sda6 on /boot type ext3 (rw)
/dev/mapper/lv-home on /home type ext3 (rw)
/dev/sda5 on /media/win_d type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/win_e type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

et cetera... As you can see, my SATA disks are recognized as sda* and sdb*. 

At this point though, finding a windows machine and formatting it that way as suggested above would be a good idea as well. :|

---

### Post by Sef on 2007-12-23
> Could you post the output of fdisk -l please?

Here it is

> /dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        4255    24410767+  83  Linux
/dev/hda3            4256        4377      979965   82  Linux swap / Solaris

Disk /dev/sda: 8254 MB, 8254389760 bytes
255 heads, 63 sectors/track, 1003 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1004     8060896    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1002, 254, 63) logical=(1003, 137, 29)



---

### Post by der_joachim on 2007-12-23
In that case, your USB stick is /dev/sda indeed. The mount command posted above should work. Although i do not know what the following line in your fdisk output means:

> 
Partition 1 has different physical/logical endings:


I do think however that whatever that line means, that may be at the root of your problem.

---

### Post by Sef on 2007-12-24
I tried to reformat it with my computer at work. (XP is on it.)  However, it said that the usb is locked.   What can I do?


> In that case, your USB stick is /dev/sda indeed. The mount command posted above should work. Although i do not know what the following line in your fdisk output means:

Quote:
Partition 1 has different physical/logical endings:
I do think however that whatever that line means, that may be at the root of your problem. 

I agree.

---

### Post by PreviousN on 2007-12-24
I'd recommend sticking with ubuntu to format it. Heres what you do:

1. Put the drive in. It'll show up on the desktop or something...right?
2. Open a "terminal". Type this: "sudo umount -a" (this is likely what windows means. Locked device might mean that its in use. If you unmount it, it will no longer be in use).
3. I like gparted. Its really convenient. But you can use whatever disk util you want. But I'm going to give you steps for gparted, particularly because I like it. Just so you know. Also, **be very careful with these tools, like fdisk/gparted/cfdisk. They delete everything from a drive. Make sure you've got the right drive. Back up important data. a slip of hand and you've got everything gone**

Ok. so.. get gparted. In a terminal: "sudo apt-get install gparted"

4. sudo gparted /dev/sda
5. Right click on the grayed area (where there's supposably data) and select "delete"
6. Click apply. This deletes everything. be sure that this is what you want to do!!!!
7. Now, right click on the empty space and choose "format". Since its a flash drive, choose "fat32" for the drive. This allows it to be compatable with windows/mac/linux computers. 
8. Hit apply. 
9. You've now got a freshly formatted flashy drive. :-) 

Good luck. Hope this helps you out a bit. Cheers!!!!111!



Oh, and for the guy above:
Quote:
Partition 1 has different physical/logical endings. 

This means your partition table on the flash drive is messed up. I would personally format a drive that has this error message because it could be unstable/you never know what is going on.

---

### Post by Sef on 2007-12-25
The only way I have gotten it be read/write is with Knoppix.  I need to find the command, so I will be able to use the root terminal.   (I figure i can go to Knoppix and find it; or at google it.)  

No other way has allowed me to get into make it read/write.  It othewise remains read only.

Update: I did dmesg |tail which indicates the write protect is on.  Is there a way via the terminal to turn Write Protect off?

> sef@jokat1:~$ dmesg |tail
[21773.493627] sd 6:0:0:0: Attached scsi generic sg0 type 0
[21773.573923] sd 6:0:0:0: [sda] 16121855 512-byte hardware sectors (8254 MB)
[21773.574765] sd 6:0:0:0: [sda] Write Protect is on
[21773.574771] sd 6:0:0:0: [sda] Mode Sense: 0b 00 80 00
[21773.574775] sd 6:0:0:0: [sda] Assuming drive cache: write through
[21773.577832] sd 6:0:0:0: [sda] 16121855 512-byte hardware sectors (8254 MB)
[21773.580501] sd 6:0:0:0: [sda] Write Protect is on
[21773.580505] sd 6:0:0:0: [sda] Mode Sense: 0b 00 80 00
[21773.580508] sd 6:0:0:0: [sda] Assuming drive cache: write through
[21773.580513]  sda: sda1


---

### Post by PreviousN on 2007-12-29
have you tried opening up a terminal and typing: 

"sudo -i"

This gives you a root terminal. You should have write permissions on everthing. If not, then You could try checking the permissions? You may have an obscure owner/555 permissions. 

You may try:
sudo -i && chmod 777 -R [insert drive here]

???

---

### Post by Sef on 2007-12-29
> You may try:
sudo -i && chmod 777 -R [insert drive here]


When I do that, should my usb drive be mounted or unmounted?

---

### Post by Sef on 2008-01-05
It's working now.  There is an lock/unlock switch on there.   After reformatting it on Ubuntu, it would not be seen, so I reformatted it on my work computer, which has XP on it.  It works fine now.

---

