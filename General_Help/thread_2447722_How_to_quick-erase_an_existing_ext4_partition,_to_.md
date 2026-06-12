---
title: "How to quick-erase an existing ext4 partition, to make it empty and fresh as new?"
date: 2020-07-24
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2020-07-24
Howdy,

I have a few drives that I have been using for system backups. Im going to redo my backup scheme so I want to scrap everything that's on these drives already and start out fresh with empty file systems.

As there are millions of files on these drives, to delete all the files on them would take forever and who knows if it could lead to corruption or not. Basically I just want to start over again with fresh empty file systems.(*)

Also I do not recall all the steps I went through to set up the drives in the first place, I was following various recipes. Somehow I managed to get them partitioned, encrypted, mapped by /dev/mapper, and given entries in /etc/fstab and /etc/crypttab with UUIDs, to auto-mount using keyfiles to open/mount. I am afraid anything I might do would break some aspect of all of this. (Sorry for the n00b question)

Can I use the mkfs.ext4 command to just wipe one of these partitions clean and not break the rest of the setup?  The drives are on external devices, encrypted with LUKS2. They are not part of a logical volume scheme.

For example, this is what one of them looks like in lsblk:

```

sdb                       8:16   0   4.6T  0 disk  
&#9492;&#9472;sdb1                    8:17   0   4.6T  0 part  
  &#9492;&#9472;backup2            253:7    0   4.6T  0 crypt /media/user/backup2
```

Somehow I have also mapped this drive to /dev/mapper/backup2, but I dont recall how I did that. Just following recipes. 

Is there a simple command I could issue to just redo the file system on this drive from scratch while not messing anything else up?

Rabu

(*) 
I have found however for anyone interested, that the fastest way to delete all the files in a directory is to rsync the directory with an empty directory, much faster than rm or find -exec rm. 
eg
mkdir empty
rsync -a --delete empty/ directorytodelete/

---

### Post by ActionParsnip on 2020-07-24
Its a common trick. You can do the same in Windows using robocopy to delete a folder when the file path is longer than 255 characters and Windows cannot use it

---

### Post by pbear42 on 2020-07-24
I must be missing something.  Isn't the simple answer to reformat the drives?  You can do that easily with Disks or GParted (or CLI, for that matter).

---

### Post by Ranbunta_Bantubunt on 2020-07-25
> **pbear42 said:**
> I must be missing something.  Isn't the simple answer to reformat the drives?  You can do that easily with Disks or GParted (or CLI, for that matter).

The complicating factors are the encryption system, auto-mounting on startup and with mount command, and my being a relative n00b.

I did the following and it seemed to work:

A) 
unmount existing drive/partition

B) 
open crypt container

cryptsetup open /dev/sda1 --key-file (keyfile path) backup2

C)
make new file system in that container, over-writing the old one:

mkfs.ext4 -L backup2 /dev/mapper/backup2

proceed anyway - type y

seems to have done the trick.

this may be really obvious to people who know what they're doing, but alas I am not such a person :)

---

### Post by Ranbunta_Bantubunt on 2020-07-25
well I thought I had succeeded, but looks like actually I messed everything up as I had feared. 

After issuing the mkfs.ext4 command, the filesystem was there and worked fine, mounted where expected, but when it was unmounted and I tried to remount it I get this error:

```

mount: /media/user/backup2: wrong fs type, bad option, bad superblock on /dev/mapper/backup2, missing codepage or helper program, or other error.

```

and

```

cryptsetup open /dev/sdc1 --key-file (path to keyfile) backup2
Device backup2 already exists.

```

(the drive is on /dev/sdc now)

any ideas how to get out of this trouble? do i need to update my /etc/crypttab and /etc/fstab entries?

---

### Post by Ranbunta_Bantubunt on 2020-07-25
well I removed it from /dev/mapper with dmsetup remove then opened it again with cryptsetup open, then I was able to mount again

---

### Post by HermanAB on 2020-07-25
The disks are encrypted, the data is randomized.  So all you need to do is hit yourself upside the head with a brick to forget the password.

---

### Post by sudodus on 2020-07-25
*Will you continue to use the drives, or do you intend to sell the drives or give them to somebody else?*

1. If you will continue to use the drives, then just make a new partition table and new file system(s), for example with gparted when booted from another drive. It is a quick process, and you can reuse the drives.

2. If you intend to sell the drives or give them to somebody else, remapping of the connection between the logical adresses and physical memory locations is the best way to make the old content impossible to read. If the drives were encrypted before, no worries, as described by HermanAB.

There is also a method via `hdparm` to use a built-in tool in SATA drives for this purpose (to remap the connection between the logical adresses and physical memory locations). But if the drives are connected via USB, this remapping method can destroy the drives, so stay away from it.

---

### Post by Ranbunta_Bantubunt on 2020-07-25
thank you

---

