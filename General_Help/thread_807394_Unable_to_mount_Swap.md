---
title: "Unable to mount Swap"
date: 2008-05-25
forum: General Help
---

### Post by Zer0Nin3r on 2008-05-25
Hello, after I tried (unsuccessfully) to wake my laptop from sleep, I am noticing that my encrypted swap partition is not being mounted upon boot up, even after restarts.  I notice the following error message:

> hda6_crypt: the check for '/dev/mapper/hda6_crypt' failed. /dev/mapper/hda6_crypt contains data: - The device /dev/mapper/hda6_crypt contains a valid file system type suspend

I am running a Compaq R300 with 512MB of RAM.  I am experiencing application crashes due to not enough memory and I would like to correct this.  Any thoughts?

**Update**
Okay so I found and checked a HowTo and everything is in check.  I still however receive the same error message when I go to mount the swap.  I don't know how to access the swap and delete any files/images that may have been saved there.

[via '/usr/share/doc/cryptsetup/CryptoSwap.HowTo']
```
This document describes how to configure an encrypted swap partition
on Debian systems. An encrypted swap partition prevents spying on
plaintext secrets (passwords) that may be written to disk when memory
is swapped to disk.

First deactivate your swap: swapoff -a

Your /etc/fstab file should have a swap entry like this (/dev/hda9
might be a different partition on your system):
# <file system> <mount point>   <type>  <options>     <dump>  <pass>
/dev/hda9        none           swap    sw            0       0

Now just replace /dev/hda9 (or whatever your swap own partition is)
with the new device name /dev/mapper/cswap:
# <file system> <mount point>   <type>  <options>     <dump>  <pass>
/dev/mapper/cswap  none         swap    sw            0       0

After that add an entry in /etc/crypttab (replace /dev/hda9 with
your own swap partition):
# <target name> <source device>	<key file>	<options>
cswap		/dev/hda9	/dev/random	swap,cipher=aes-cbc-plain,size=128,hash=ripemd160

Now start your crypted device:  /etc/init.d/cryptdisks start
And reaktivate your swap:       swapon -a

Thats it! You have a crypted swap device. Note that the
/dev/random device might not generate enough random bytes, so the boot
process can wait indefinitely unless you press some keys on your
keyboard. To be sure that booting is not interrupted, use the (less
secure) /dev/urandom device instead.

Read the crypttab(5) manpage for more information, for example options
to use a different encryption algorithm than the default.

-- Bastian Kleineidam <calvin@debian.org>
```

**Update**
If I create an empty file named 'hda6_crypt' and run the command '/etc/init.d/cryptdisks start' I get the same error message and the file I created gets deleted.

**Update**

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/hda2_crypt /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ce2c986e-7937-4e5f-ad55-bdba5691c982 /boot           ext3    defaults        0       2
# /dev/hda1
UUID=2AAC8C08AC8BCCAF /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=0274D14574D13C5B /media/hda3     ntfs    defaults,umask=007,gid=46 0       1
/dev/mapper/hda6_crypt none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

cryttab
```
hda2_crypt /dev/disk/by-uuid/b1b2a0f2-2422-40c0-8449-216796b188dd none luks
hda6_crypt /dev/disk/by-uuid/74cc1b18-53d3-4ece-ac72-33d021b12620 none luks,swap
```

**Update**
Alright, so I've managed a temporary fix for the moment.  I have reformatted the encrypted swap to unencrypted and mounted it all within Gparted.  While this will work for now, the swap is vulnerable to "snooping" should something happen.

Now I just need to figure out how to re-encrypt the swap, and get it to mount again.

---

### Post by ibuclaw on 2008-05-25
Try typing into the terminal:
```
sudo swapon -a
```

Do you get any error messages?

Regards
Iain

---

### Post by Zer0Nin3r on 2008-05-25
> **tinivole said:**
> 
Do you get any error messages?


I get the following: 

> swapon: cannot canonicalize /dev/mapper/hda6_crypt: No such file or directory
swapon: cannot stat /dev/mapper/hda6_crypt: No such file or directory

It's related to there being an image file stored on the swap from when I placed my laptop in suspend mode.  I was trying to see if suspend worked, as I have been having problems with suspend ever since 7.04.  Thank you though.  I have to figure out how to clear the swap somehow.

---

### Post by VMC on 2008-05-25
> **tinivole said:**
> Try typing into the terminal:
```
sudo swapon -a
```

Do you get any error messages?

Regards
Iain

If that doesn't work you might try just removing swap altogether and rebuild:
mkswap /dev/hdax
swapon /dev/hdax

x=whatever you want swap partition

---

### Post by Zer0Nin3r on 2008-05-25
Hehe.  Performed the following:

```
jigga@R3000:~$ sudo mkswap /media/hda1/temp/swap 1048576 -f
Setting up swapspace version 1, size = 1073737 kB
no label, UUID=563ff834-b4f5-44d1-bf43-3cbf2c03a050
jigga@R3000:~$ swapon -a
swapon: cannot canonicalize /dev/mapper/hda6_crypt: No such file or directory
swapon: cannot stat /dev/mapper/hda6_crypt: No such file or directory

```

Can I go ahead and delete the file '/media/hda1/temp/swap'?  Also are there any other changes that I need to make in order to undo what I just did?

---

