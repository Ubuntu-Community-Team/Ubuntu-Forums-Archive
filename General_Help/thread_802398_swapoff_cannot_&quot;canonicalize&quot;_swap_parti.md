---
title: "swapoff cannot &quot;canonicalize&quot; swap partition"
date: 2008-05-21
forum: General Help
---

### Post by Roobert on 2008-05-21
I was checking the usage of system resources on my system, and noticed that the swap was not turned on. Checking my /etc/fstab, I could see that there was an entry to turn on the swap at bootup, but for some reason this wasn't happening:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=ba15734d-04ef-41c4-b46b-08dad8db0bc7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=929b42fb-5351-4a32-929b-2b2032e88a30 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=07D7-0302  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=640CE4A40CE4728A /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=0A3C4E8A3C4E712D /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=fdaf7827-6962-4c95-89e6-e615c39966bd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

As you can see, there is an entry at /dev/sbd6 to turn the swap on. Trying to turn it on from the from the command line, I received an error:

```
sudo swapon -a
swapon: cannot canonicalize /dev/disk/by-uuid/fdaf7827-6962-4c95-89e6-e615c39966bd: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/fdaf7827-6962-4c95-89e6-e615c39966bd: No such file or directory
```

What does this error mean? Any ideas on how to get my swap to turn on at bootup?

Thanks,

~ Eric.

---

### Post by cdtech on 2008-05-21
Try running "blkid" from a command line and copy your UUID for swap, copy and paste into your "fstab" file. Or you could just use the /dev/name instead of the UUID.

---

### Post by Roobert on 2008-06-10
Thanks, using the /dev/name directly worked. My swap is now mounted on bootup.

Cheers,

~ Eric.

---

### Post by palito1980 on 2009-01-14
Got the same problem but I cannot figure out the way to fix it. Could you give more details about your last post in this thread?

---

### Post by unutbu on 2009-01-14
First, open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l
```

You will see lines like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455    10602899     5245222+   b  W95 FAT32
/dev/sda3   *    10602900    51568649    20482875   83  Linux
[COLOR="Red"]/dev/sda8[/COLOR]       621040833   625137344     2048256   82  [COLOR="Red"]Linux swap / Solaris[/COLOR]
```

Look for the line whose System type is "Linux swap / Solaris".
Look for the corresponding Device. In the example above, it is /dev/sda8.

Now edit /etc/fstab. To launch an editor as root:
```

gksu gedit /etc/fstab
```

Look for a line whose 3rd field says "swap":
```

UUID=bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5 none [COLOR="Red"]swap[/COLOR]    sw              0       0

```
This specifies the swap partition by its UUID. If you plan to plug/unplug external hard drives from your system, then we should work on fixing the UUIDs. If your system's hardware is fixed, then it is okay to use device names, as mentioned in Roobert's post #3.

To use device names:

"Comment out" the line in /etc/fstab by addng "#" to the beginning of the line
```

# UUID=bcbf2c68-7c2d-4e9d-bf4b-bdc6f3ee74c5 none swap    sw              0       0
```

This tells the system to ignore this line. Then add a new line
```

/dev/sda8 none swap    sw              0       0
```

Change /dev/sda8 to the correct device name, as you found above in the output of "sudo fdisk -l".

---

### Post by palito1980 on 2009-01-14
I think that your advice was helpful because when I typed "sudo swapon -a" it asked for a sudo password and nothing else happened I mean no errors. I consider your advice very helpful. Thank you very much.

I have one more question: 

Where can I find, in ubuntu, boot log? There are some problems with fat system on my windows partitions.

---

### Post by unutbu on 2009-01-14
I'm glad your swap problem appears to be resolved.

For boot logs, check /var/log/messages*, /var/log/syslog*, and /var/log/dmesg*.

---

### Post by oscar-cortes on 2009-05-28
thanks a lot... I had the same problem, I hope this help me... now swap seems to work

---

