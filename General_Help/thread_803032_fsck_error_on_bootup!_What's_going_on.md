---
title: "fsck error on bootup! What's going on?"
date: 2008-05-21
forum: General Help
---

### Post by themightymegatron on 2008-05-21
Whenever I boot, it for some reason goes into a scrolling prompt, which at one point stops and this is displayed:

> fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=6a0c4134-f304-477a-a89c-f5b8b32dbb6f'


followed by something about repairing the filesystem manually, then asks for a root password or to hit control-d to resume normal boot. I get the same error spit at me when I get booted into X and try to run fsck from the gnome-terminal. What can I do?

Edit: I've traced the error in question to the file mentioned above. /sbin/fsck.ext3. Have no clue what to do with that though...

---

### Post by niteshifter on 2008-05-22
Hi,

What's going on is that every so many boots fsck (file system check) is run. It has run and can not find the drive's partition with that UUID.

fsck fronts for a variety of particular file system checkers, in this case the one for ext3 file system (fsck.ext3).

Now, as to how to fix this, we need some information. And you'll need a Live CD as running fsck on a mounted file system can lead to Bad Things.

Boot the system normally, the Live CD use will come later. Open a terminal window, run the below commands and post the output of them here, please:

```
cat /etc/fstab
```

```
sudo fdisk -l
```
That's a lower case L not a the digit 1 in the above.

---

### Post by plucky on 2008-05-22
> Whenever I boot


Do what **niteshifter** says and also add ```
ls -l /dev/disk/by-uuid
``` That is lowercase L not a 1, so we can see what your partition UUID's are.


Good Luck

---

### Post by zvacet on 2008-05-22
> Unable to resolve 'UUID=6a0c4134-f304-477a-a89c-f5b8b32dbb6f'

To fix this run 

```
sudo blkid
```

after that 

> gksudo gedit /etc/fstab

Compare UUID from blkid command with ones in fstab.Replace one which is wrong in fstab with coresponding one from blkid.Save file and close it.This should solve your problem.

---

### Post by themightymegatron on 2008-05-22
Thanks to everyone for your help! My partition sda7 was for some reason mislabeled in 
> /etc/fstab

by running 

> ls -l /dev/disk/by-uuid

I was able to acquire the proper UUID and edited /etc/fstab accordingly. Everything's working fine now! Thanks a bunch guys!

---

