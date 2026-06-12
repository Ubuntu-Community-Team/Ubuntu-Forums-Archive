---
title: "How to delete all files &amp; directories from broken distro installation"
date: 2014-07-31
forum: General Help
---

### Post by Kirkx on 2014-07-31
I have broken my Linux Lite and it has to be re-installed from scratch. As I'am using Grub4Dos to boot all my distros, I don't want to format the root and home partitions when reinstalling so that the device numbers of all partitions remain intact. After booting to Xubuntu, what would be the best commands to delete all files and directories in the broken OS before fresh re-install. Is this enough:

```

rm -rf /media/user_name/broken_os_folder/*
rm -rf /media/user_name/broken_os_folder/

```
or:
```

rm -rdf /media/user_name/broken_os_folder/*
rm -rdf /media/user_name/broken_os_folder/

```

In my case the broken OS is installed to:
```

/dev/sda21
/dev/sda22

```

I don't worry about Grub2, MBR and all that, because, as mentioned before, I'm using Grub4Dos to boot to all my distros, completely bypassing Grub2. In case someone is curious how to do it here is Menu.lst:

```

# Grub4Dos file Menu.lst
title Xubuntu
root (hd0,22)
kernel /boot/vmlinuz-3.13.0-32-generic root=UUID=4ghka89-5586-3b77-8r6c-49f28g17d4n9 ro
initrd /boot/initrd.img-3.13.0-32-generic

```

---

### Post by sudodus on 2014-07-31
Before doing things like this you should ***backup everything valuable*** (personal files like photos, documents etc). You might make a mistake and remove data from the wrong partition.

I think these  are separate partitions that you want to wipe clean.

I don't think it is necessary to wipe the partition to make it unreadable for security reasons. In this case you can

- boot from another drive, for example a DVD/USB drive with an Ubuntu desktop install system

- start ***gparted*** and simply format the two partitions 

```
/dev/sda21
/dev/sda22
```

to the file systems you want. Then the files won't be there, and they are clean for a new installation. This is much more efficient than using the rm command. (But the content of some of the files can be recovered with a tool like PhotoRec.)

---

### Post by coffeecat on 2014-07-31
> **Kirkx said:**
> I don't want to format the root and home partitions when reinstalling so that the device numbers of all partitions remain intact.

If you simply reformat the partitions, their device numbers - I assume sda21 and sda22 - should remain the same. They are only likely to change if you actually delete the partitions with gparted and then re-create them. Their UUIDs will change if you reformat, but that doesn't appear to be a problem for you as you are using partition numbers for the root line in your grub4dos menu.lst rather than UUIDs.

---

### Post by Kirkx on 2014-07-31
> **Coffeecat**: If you simply reformat the partitions, their device numbers - I assume  sda21 and sda22 - should remain the same. They are only likely to change  if you actually delete the partitions with Gparted and then re-create  them. Their UUIDs will change if you reformat,
Thanks, that's correct, I have confused formatting with deleting/re-creating. I've just tested this using Gparted Live CD and it works as follows:

a) formatting a partition - device number remains the same, UUID will change
b) resizing a partition    - both device number and UUID remain the same
c) deleting and re-creating a partition in the same location on the hard disk - both device number and UUID will change

There is one more scenario that I'm not sure about:

d) restoring a partition from Clonezilla disk image - ?

> Their UUIDs will change if you reformat, but that doesn't appear to be a  problem for you as you are using partition numbers for the root line in  your grub4dos menu.lst rather than UUIDs

With Grub4Dos you are actually using the device number in the root line and UUID in the kernel line, but under normal conditions this is not an issue because they never change. The only thing that must be occasionally manually edited is the kernel version (after each kernel update), but that's a small price to pay for freedom from Grub2 scripts.

---

### Post by coffeecat on 2014-07-31
> **Kirkx said:**
> With Grub4Dos you are actually using the device number in the root line and UUID in the kernel line, but under normal conditions this is not an issue because they never change.

My apologies - I hadn't noticed the UUID in the kernel line. Yes, you would need to edit this if you reformat your root partition. 

From what you have posted it looks as though grub4dos uses the old legacy grub syntax for its menu.lst. In which case, if my memory is correct, you could probably use /dev/sdXY in the kernel line and/or the UUID in the root line.

I've never used clonezilla, so I can't help you with that.

---

### Post by sudodus on 2014-07-31
> **Kirkx said:**
> Thanks, that's correct, I have confused formatting with deleting/re-creating. I've just tested this using Gparted Live CD and it works as follows:

a) formatting a partition - device number remains the same, UUID will change
Yes> 
b) resizing a partition    - device number remains the same, UUID will change
UUID will also remain the same> 
c) deleting and re-creating a partition in the same location on the hard disk - both device number and UUID will change
Well, device number might be the same or change> 
There is one more scenario that I'm not sure about:

d) restoring a partition from Clonezilla disk image - ?
Assuming there is already the old partition, that you rewrite to, the device number will remain. UUID is backed up, so it will remain the same.
 > 


With Grub4Dos you are actually using the device number in the root line and UUID in the kernel line, but under normal conditions this is not an issue because they never change. The only thing that must be occasionally manually edited is the kernel version (after each kernel update), but that's a small price to pay for freedom from Grub2 scripts.

For ext file systems you can identify the UUID in **/boot/grub/grub.cfg** and **/etc/fstab** and write that string into the partition with

```
tune2fs -U string /dev/sdxy
```

where x is the drive name and y is the partition number, or do the change the other way around, enter the new UUID into /boot/grub/grub.cfg and /etc/fstab

---

### Post by Kirkx on 2014-07-31
Thanks for all your tips, Sudodus. I've meade an edit in p b) in my previous post, it was a misprint.
> **coffeecat:** From what you have posted it looks as though grub4dos uses the old  legacy grub syntax for its menu.lst. In which case, if my memory is  correct, you could probably use /dev/sdXY in the kernel line and/or the  UUID in the root line.
Yes, it's the legacy syntax, you can combine root and kernel lines. So instead of this code:
```

# Grub4Dos file Menu.lst
title Xubuntu
root (hd0,22)
kernel /boot/vmlinuz-3.13.0-32-generic root=UUID=4ghka89-5586-3b77-8r6c-49f28g17d4n9 ro
initrd /boot/initrd.img-3.13.0-32-generic

```
you can use this one:
```

# Grub4Dos file Menu.lst
title Xubuntu
kernel (hd0,22)/boot/vmlinuz-3.13.0-32-generic root=UUID=4ghka89-5586-3b77-8r6c-49f28g17d4n9 ro
initrd /boot/initrd.img-3.13.0-32-generic

```
There are other ways to go about it, I haven't explored them all. The two versions shown above are fast and reliable.

---

