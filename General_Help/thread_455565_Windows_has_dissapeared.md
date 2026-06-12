---
title: "Windows has dissapeared"
date: 2007-05-26
forum: General Help
---

### Post by Jim_1981 on 2007-05-26
Maybe I should count my blessings... ;)

I was running kubuntu dapper dual booting with windows xp (using grub to select). now I've upgraded to Ubuntu Feisty. I was hoping it would just be a case of deleting the kubuntu partition and installing feisty in its place, but I had problems with the grub menu. (I have a main 200gb sata hard disk, partitioned down the middle for windows and linux, and 2 other pata ntfs hard disks.)

I was installing feisty with the alternate install disk and when it got to the grub installation it would confirm that windows was there, but I couldn't get it to work. So I disconnected the pata disks leaving just the main disk with both OS's on.

Installing ubuntu again worked and it now boots. Trouble is, windows isn't recognized at all now. No grub entry. No mount within linux (I've installed ntfs support and the other 2 disks work now I've plugged them back in) 

Here's the contents of fdisk -l:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS <----- The disk is there, but no cigar ;)
/dev/sda2           12749       24553    94823662+  83  Linux
/dev/sda3           24554       24792     1919767+  82  Linux swap / Solaris

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        5004    40194598+   7  HPFS/NTFS

Cheers :)

---

### Post by Happy_Man on 2007-05-26
Have you tried force mounting it?

```
sudo mkdir /media/test
sudo mount -t ntfs-3g /dev/sda1 /media/test
```

---

### Post by dbott67 on 2007-05-26
If that fails, you could always run fixmbr from the Windows Installation CD:

1. Boot the system from the Windows CD.
2. Select R to repair/recover
3. Get to command prompt
4. Type fixmbr
5. Reboot

Here's the caveat: FIXMBR nukes the master boot record, effectively destroying grub and preventing access to your linux partition.  After this, you would need to boot from a Live CD of Ubuntu and restore grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

-Dave

---

### Post by Jim_1981 on 2007-05-26
Cheers :)

Is there a way to install grub from the alternate install CD?

---

### Post by Jim_1981 on 2007-05-26
> **Happy_Man said:**
> Have you tried force mounting it?

```
sudo mkdir /media/test
sudo mount -t ntfs-3g /dev/sda1 /media/test
```

I tried this and here's what I got. I've got to say, it doesn't look good...

Unexpected clusters per mft record (-1).
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by dbott67 on 2007-05-26
> **Jim_1981 said:**
> Cheers :)

Is there a way to install grub from the alternate install CD?

I don't know for sure, but I just found this site:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's only a 400 kB download and can be copied to floppy, USB or burned to CD.

-Dave

---

### Post by Happy_Man on 2007-05-26
> **Jim_1981 said:**
> I tried this and here's what I got. I've got to say, it doesn't look good...

Unexpected clusters per mft record (-1).
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Dude... that's not cool. Basically it's saying that that partition is hosed. Damn....

---

### Post by Jim_1981 on 2007-05-26
> **Happy_Man said:**
> Dude... that's not cool. Basically it's saying that that partition is hosed. Damn....

Please tell me you're kidding... Is there any hope for my data at all???

---

### Post by dbott67 on 2007-05-26
> **Jim_1981 said:**
> Please tell me you're kidding... Is there any hope for my data at all???

Try the fixmbr thing first.

If that fails, stop everything and do the following:

1. Remove the hard drive and install it as a secondary drive in another Windows machine.

2. Download PC Inspector File Recovery from this site (it's free):
[http://www.pcinspector.de/file_recovery/uk/welcome.htm](http://www.pcinspector.de/file_recovery/uk/welcome.htm)

3. The process can recover lost partitions and lost files.  I've used it multiple times on client PCs to save the day.

Read this [success story]("http://ubuntuforums.org/showthread.php?p=1669037&highlight=pc+file+inspector#post1669037") right here in our forums.

-Dave

---

### Post by dbott67 on 2007-05-26
And if the post above fails, get your hands on a copy of Hiren's Boot CD:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

-Dave

---

### Post by Jim_1981 on 2007-05-28
The xp recovery console fixed it with the fixboot command. Buying a proper backup system tomorrow ;)

---

