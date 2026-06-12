---
title: "floppy permisions"
date: 2015-04-09
forum: General Help
---

### Post by ethan26 on 2015-04-09
Hi people, i need to write MS-DOS 6.22 to a floppy on ubuntu but i am have permission trouble. yes i tried sudo root chmod chown and others. i try stuff like:
```
sudo chown -v -R $USER:$USER '/media/floppy0'
```
but it says:
```
ethan@ethan-E6610:~$ sudo chown -v -R $USER:$USER '/media/floppy0'
[sudo] password for ethan: 
chown: changing ownership of ‘/media/floppy0’: Operation not permitted
failed to change ownership of ‘/media/floppy0’ from root:root to ethan:ethan
ethan@ethan-E6610:~$ 

```
i tried:
```
ls -la /media/floppy0
```
but got:
```
total 11
drwxr-xr-x 2 root root 7168 Dec 31  1969 .
drwxr-xr-x 4 root root 4096 Mar  8 19:23 ..
```
Thanks in advance!

---

### Post by sandyd on 2015-04-10
How are you writing MSDOS?

You should only need to dd the image files to your floppy device

---

### Post by ethan26 on 2015-04-10
i am mounting the Disk1.ima and opening it. then draging the files from there into the floppy

---

### Post by The Cog on 2015-04-10
FAT doesn't support unix ownershp permissions. You need to specify the permissions as part of the mount command, and they then apply to the whole filesystem.

Adding **-o umask=0** to the mount command should make the disk writable by everybody.

---

### Post by ethan26 on 2015-04-10
```
ethan@ethan-E6610:~$ mount -o umask=0 /dev/fd0
mount: only root can do that
```

---

### Post by Holger_Gehrke on 2015-04-10
> **ethan26 said:**
> i am mounting the Disk1.ima and opening it. then draging the files from there into the floppy

Which wouldn't work, since you also need to write the boot sector ... unless you don't want to be able to boot from the floppy.

Just do ```

sudo dd if=Disk1.ima of=/dev/"whatever you floppy is"

```
(replace the obvious part, please) and be done with it ...

---

### Post by ethan26 on 2015-04-10
Flippin floppy disks! It worked! Yaaaay!\\:d/

---

