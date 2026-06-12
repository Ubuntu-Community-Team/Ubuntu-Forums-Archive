---
title: "What to add to Fstab to get Floppy Drive to work?"
date: 2017-11-14
forum: General Help
---

### Post by Rick St. George on 2017-11-14
Trying to copy files from bunch of Floppies. Running Xubuntu v16.04 LTS.

Tried Mtools, and get;
> 
cannot initialize 'A:'


Tried this ...
```

mount -o umask=0 /dev/fd0

```

And got this;
> 
can't find /dev/fd0 in /etc/fstab


AH HA ... but alas ... What do I add to the Fstab file ??? 
And is this all I need to get my Floppy to work in File Mgr.?

Thanks!

---

### Post by Holger_Gehrke on 2017-11-14
You forgot to give the mount command a parameter it needs: the directory to mount the drive into. If you don't give this, it looks in the fstab for it. If it doesn't find it there, it complains.
The command should have been something like;
```
mount -o umask=0 /dev/fd0 /mnt
```
Which would mount it into /mnt. You probably have to put 'sudo' in front of this command, since mounting arbitrary block devices is a privileged operation.

Holger

---

### Post by Rick St. George on 2017-11-14
> **Holger_Gehrke said:**
> You forgot to give the mount command a parameter it needs: the directory to mount the drive into. If you don't give this, it looks in the fstab for it. If it doesn't find it there, it complains.
The command should have been something like;
[code]mount -o umask=0 /dev/fd0 /mnt[code]
Which would mount it into /mnt. You probably have to put 'sudo' in front of this command, since mounting arbitrary block devices is a privileged operation.

Holger

And this is what I get ...
> 
mount: /dev/fd0 is not a valid block device


So... What line can I put in FSTAB ?

Thanks,

---

### Post by Dynamo_Joe on 2017-11-15
Right mouse click and select "Open as administrator". :) 

1. Must have disk in floppy drive. 

2. Drive is shown in the "Devices" list in the left hand panel of the file manager.

---

### Post by Holger_Gehrke on 2017-11-15
> **Rick St. George said:**
> And this is what I get ...
```
mount: /dev/fd0 is not a valid block device
```


So... What line can I put in FSTAB ?


**IF** the drive were working after this 'mount'-command, you'd put something like
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0 
```
which would tell the system to mount floppíes into the directory /media/floppy0, to recognize the filesystem on the floppy automatically, to allow reading and writing, to allow the mounting of floppies to normal users, to not try to mount the floppy when starting the system and and allow execution of programs from floppy; **but the error you got means there's something else wrong**.
Check whether the kernel-driver for the floppy drive is loaded (it often isn't, because few people use floppies anymore):
```
lsmod|grep floppy
```
If this show a line saying 'floppy' and some other stuff, the driver is loaded and I don't know what the problem is (bad disk ? loose connector ? broken cable ? defective drive ?), but if it doesn't produce any output, you need to load the module with
```
sudo modprobe floppy
```
Now try mounting the floppy again. If this works, you should add a line saying 'floppy' to the file '/etc/modules/' to make the module load automatically in the future.

Holger

---

### Post by Dennis N on 2017-11-15
Should these methods described above fail, you have the option of using a USB floppy disk drive. Available generally for less than $20. I have one, and it works without any problems.

---

### Post by Rick St. George on 2017-11-15
Did "modprobe" yesterday. ```
 lsmod|grep floppy
``` gave "Floppy  73728  0".

Tried to mount again, here is the output;

> 
Error mounting /dev/fd0 at /media/steve/disk: 
Command line 'mount -t "auto" -o "uhelper=udisks2,nodev,nosuid"
"/dev/fd0" "/media/steve/disk" exited with non-zero exit status 32:
mount: /dev/fd0 is not a valid block device.


Any suggestions?
Thanks!

---

### Post by ajgreeny on 2017-11-15
I have not had a floppy disk for many years now but when I last did use one it was much more difficult to mount it; if I remember correctly I used a udisks command, but I can now find no references to that any more.

It is probably worth your while doing a careful search of udisks to see if anything pops up that helps; **man udisks** unfortunately, is no help.

EDIT:
A quick search suggests you now need to use ```
udisksctl --mount /dev/fd0
```but I have no way to test this any more.

You might find it useful to search using my custom google-search site at [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) using the search term **udisks floppy mount** which is how I found that **udisksctl** suggestion

---

### Post by Rick St. George on 2017-11-15
Tried that Code, but the -- is not required before "mount" command. This is Code I found and used;

```

udisksctl mount -b /dev/fd0
*also tried
udisksctl mount -b /dev/fd0 -t vfat

```

And got the same output as above in Post #7.
Using lsblk shows "fd0", but of course no mountpoint.

This BUG Link [http://bugs.freedesktop.org/show_bug.cgi?id=63849](http://bugs.freedesktop.org/show_bug.cgi?id=63849) 
shows it may have been fixed in 2014 (see next to last post), but the last post asks in 2016 - is it fixed yet?
Still don't know what to do !?!?!

---

### Post by Holger_Gehrke on 2017-11-15
Let's first check a silly assumption: you do have a disk in the drive, don't you ? Don't be offended, I came across a few post in several forums while researching the error message, where that turned out to be the problem ...

Do you hear the drive making some noise (motor running, drive head getting moved) after issuing the mount command ? These thing are noisy. If it stays silent, I'd suspect the cable or the drive ...

Search the output of dmesg for floppy or fd0
```

dmesg|grep -E '(floppy|fd0)'

```
If there's a lot of complaining about unreadable or bad sectors in there, you might have a bad disk or a dirty read head.

Holger

---

### Post by yancek on 2017-11-15
In post # 9 above, you indicate the filesystem on the Floppy is vfat.  Have you verified that?  Run the command:  sudo parted -l (Lower Case Letter L in the command) which should tell you the fs type.  Then try mounting using the fs type such as below

> sudo mount -t vfat /dev/fd0 /media/steve/disk 

That should work if you have the correct fs type (vfat?) and you have a mount point directory of disk under /media/steve and your floppy is not corrupted and you won't need an entry in fstab.  When is the last time you used the floppy successfully?

---

### Post by Holger_Gehrke on 2017-11-15
Now look what you made me do ! I've actually pulled out the early 2000's era laptop that I keep around for the serial and parallel interfaces it has, looked for (and found) a floppy disk and checked whether the commands ajgreeny and I gave you worked. And they do, at least with the correction to the udisksctl command you found yourself. And since this machine runs LUbuntu 16.04, the commands should be identical.

Holger

---

### Post by Yellow Pasque on 2017-11-15
> **Holger_Gehrke said:**
> Do you hear the drive making some noise (motor running, drive head getting moved) after issuing the mount command ? These thing are noisy. If it stays silent, I'd suspect the cable or the drive 

And if the drive's light is always on, you connected the data cable upside down.
And if you see magic smoke, you probably connected the power cable off one pin ;)

---

### Post by Rick St. George on 2017-11-16
Sorry guys ... it seems my older computer is crapping out. Now it won't boot, screen is black (no signal), CD will not open, and I suspect the MOBO. Because, I have to use the switch on the PSU to turn it on and off. When I turn it on, the CPU Fan starts turning (prior to pushing the Start Button on the front). So if there is something wrong with the MOBO that may expain my problems with recognizing the Floppy.

Recently I simply installed a HDD from an older laptop, and low & behold it booted into Xubuntu. So thought I would use it to put some older software and data from old floppies onto the HDD then onto some DVDs for archiving. Guess I will have to find another solution, such as buying a SATA or USB Floppy Drive. Found one on Amazon.

Thanks for the info, help and research. Perhaps someone else can utilize it.

Peace,
Rick

---

### Post by Yellow Pasque on 2017-11-16
Did you unplug the floppy drive? Seriously, double check the power connector to the floppy. If you put it on incorrectly (or the drive's electronics are faulty), you can damage your PSU and other components. If you connected the drive yesterday, and now your system doesn't work, that seems like a big coincidence to swallow.

The floppy power connectors weren't very foolproof, and it can be all too easy to connect it the wrong way without using a lot of force like you would need to do with other ATX power connectors.

---

### Post by Rick St. George on 2017-11-16
Thanks Temujin, but no one messed with the connection of that floppy. However, just to make sure - I double checked. And yes, its correct.

Too bad I recently took all my old computer stuff to the Geek Squad at Best Buy. I had a spare MOBO.
Thanks to all who helped.

Rick
):P

---

