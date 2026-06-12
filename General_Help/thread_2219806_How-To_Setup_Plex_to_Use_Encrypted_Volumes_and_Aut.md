---
title: "How-To Setup Plex to Use Encrypted Volumes and Auto-mount Them at Boot Ubuntu 14.04"
date: 2014-04-25
forum: General Help
---

### Post by patrickscarroll on 2014-04-25
My setup is a fully-encrypted system with three physical hard drives.  The first is a 500gb main hard drive (with Ubuntu 14.04 installed, EXT4), a second 1.5tb storage drive (EXT4), and a third 2.0tb storage drive(EXT4).  All are encrypted with LUKS (the last two were encrypted in a previous version/install of Ubuntu).   
 
===============================
 **PROBLEM**: I want to type a single password at boot, have the other two hard drives automatically decrypted and mounted, and have Plex be able to view those encrypted drives to access my videos and music.  With the default setup in Ubuntu, where you manually click on the encrypted drives in Nautilus and enter your pass-phrase, Plex doesn't seem to be able to see my encrypted files even though I can browse them with Nautilus.

 **SOLUTION**: the following steps worked for me in Ubuntu 14.04 (fresh install of Ubuntu, choosing the encrypt entire drive option on my 500gb drive)...

**Note**: there is also a way to do this all with a GUI, using the "Disks" or gnome-disk-utility built-into Ubuntu 14.04 by editing the encryption and mount options for the LUKS partitions (though I haven't gotten that to work as reliably as the method below). The steps I've shown below are the _manual_ way of doing it using the terminal.

**Note**: this isn't necessarily just for plex media server users, but is a general guide for automatically mounting encrypted drives in Ubuntu.
 ===============================

1. Install and setup the Plex media server as you normally would, if it's not already installed (I'm using version 0.9.9.10.458).

2. Gather information about your encrypted drives, which we will use later...

```
sudo blkid
```

This  will list all of the device names and UUIDs of your drives.  For  example, my list is this (**Note**: I've replaced the UUIDs with x's for privacy purposes, and only  listed the main partitions)...

```
/dev/sda1: UUID="xxx-xxx" TYPE="vfat"
/dev/sda2: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="ext2"
/dev/sda3: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="crypto_LUKS"
/dev/sdb1: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="crypto_LUKS"
/dev/sdc1: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="crypto_LUKS"
```

Drive #1: sda1, sda2 are the first couple non-encrypted partitions on my 500gb drive, and sda3 is the encrypted partition of the root of my system.
Drive #2: sdb1 is the encrypted partition of my 1.5gb encrypted terabyte drive
Drive #3: sdc1 is the encrypted partition of my 2.0gb encrypted terabyte drive

Keep the partition info (such as "/dev/sdb1") and the UUID info for each partition handy for use later on.

3. Create a random key-file (basically a random, really-long pass-phrase stored in a file).  This key will be added to your encrypted volume(s) as a second key for unlocking the drive. The first was the pass-phrase you used initially to encrypt the drive.  We will create a second one for automatic mounting.  This file will be stored in your root folder on your main encrypted drive, so will be protected by that boot-up pass-phrase...
 
```
sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4
```

**Note**: if you already created a key-file previously for your encrypted drive and added it (sometime in the past), just skip this step.  Copy a backup of the key-file to your root directory, perform step #4 then skip to step #6.

 4. Change the permission of that file to be read-only by root...
 
 ```
sudo chmod 0400 /root/keyfile
```
 
5. Add the key-file to LUKS for my two encrypted terabyte drives (sdb1 and sdc1 are the names of the LUKS encrypted partitions on my system, your's might be different)...
 
 ```
sudo cryptsetup luksAddKey /dev/sdb1 /root/keyfile
sudo cryptsetup luksAddKey /dev/sdc1 /root/keyfile
```
 
 [**NOTE**: you will be prompted for the pass-phrase that you used to originally encrypt each of those drives, and this keyfile will be added as a second way to unlock the drive.  Therefore, you should protect this file carefully just as you would protect the origional pass-phrase.  The keyfile will be stored on your encrypted main system, protected by whatever pass-phrase you used to unlock your system at boot.  It will only be accessible by root.  If someone can get access to this file, then you have more serious security problems already.]  
 
 6. Setup crypttab to configure and decrypt the volumes at boot...
 
```
sudo gedit /etc/crypttab
```
 
Add the following lines (Replace "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" with the UUID of each drive)...
 
```
#My Second Drive
sdb1_crypt UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /root/keyfile luks,discard,nofail
 
#My Third Drive
sdc1_crypt UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /root/keyfile luks,discard,nofail
```
 
 7. Create two folders in the &#8220;/media&#8221; folder to allow access to the decrypted portion of the drives (I picked &#8220;mydrive2&#8221; and &#8220;mydrive3&#8221; but you could use anything)...
 
```
sudo mkdir /media/mydrive2
sudo mkdir /media/mydrive3
```
 
8. Setup fstab to mount the decrypted drives at boot...
 
```
sudo gedit /etc/fstab
```
 
Add the following lines...
 
```
#My Second Drive
/dev/mapper/sdb1_crypt /media/mydrive2 ext4 defaults 1 2
 
#My Third Drive
/dev/mapper/sdc1_crypt /media/mydrive3 ext4 defaults 1 2
```
 
 9. Reboot!

That's it, just add your media in Plex (after rebooting of course) as you normally would with a non-encrypted system.
 
=====================
 Please leave any feedback about the how-to I've created, and I'll change it accordingly.  Is this secure?  Is this the best way to set this up?  I've put this together from several sources, so thanks to the Ubuntu community!

---

### Post by finger51 on 2014-06-19
Hi, all went well for me until mount- 
```

mount: special device /dev/mapper/sdb_crypt does not exist

```

and sure enough, there is nothing there:
```

$ ls /dev/mapper
**control**

```

I don't have any partitions on this drive, so no number after sdb... would that make a difference?
```

$ sudo blkid

/dev/sdb: UUID="*xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx*" TYPE="crypto_LUKS"

```

 I was able to mount this drive manually before trying this out. Used trueCrypt if that makes a difference.
thanks for the write up!

---

