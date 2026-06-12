---
title: "Mediatomb not seeing files on second drive at startup"
date: 2013-08-17
forum: General Help
---

### Post by evilbrent on 2013-08-17
Hi,

Every time I restart my computer I have to go into mediatomb and re-add the folder which has my movies on it. It's on a second drive.

I suspected that it's something to do with that drive not being mounted at startup so I used the program automount to set it to mount, but didn't help.

Can anyone give me any ideas about how to get the folder to appear in mediatomb after starting up?

Thanks.

---

### Post by zero2xiii on 2013-08-18
Hay,

Please post the output of (in code brackets):
```
lsblk
sudo blkid
cat /etc/fstab
```

I assume the drive is not being mounted by fstab.
The first command shows us all the partitions (block devices) on your system.
The second command needs sudo to execute - it gives us the UUID's of all the current connected drives. This is needed to format the fstab line.
The third command shows us the content of your current fstab file.

After that we should be able to give you the string to add to the fstab to mount your drive at boot.

Thanks :)

---

### Post by evilbrent on 2013-08-18
Thank you. 

```
brent@Martha:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0 891.7G  0 part /
&#9500;&#9472;sda2   8:2    0  31.4G  0 part /media/867CF7DF7CF7C847
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   8.5G  0 part [SWAP]
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part /media/2TB

```

```
brent@Martha:~$ sudo blkid
[sudo] password for brent: 
/dev/sda1: UUID="1ebe4b97-567b-457a-bc83-40ef54677229" TYPE="ext4" 
/dev/sda2: UUID="867CF7DF7CF7C847" TYPE="ntfs" 
/dev/sda5: UUID="cc7b51e8-18e0-4d07-9268-c5538a2abf73" TYPE="swap" 
/dev/sdb1: LABEL="2TB" UUID="2ec2030a-5ec5-44c7-b251-a3cb78b8d853" TYPE="ext3"
```

```
brent@Martha:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1ebe4b97-567b-457a-bc83-40ef54677229 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```


The drive in question is the 2TB sdb1. There is also an XP partition and a swap area on sda.

Just looking at that, and not really knowing anything else about it, I guess I need to add a line to the fstab?

```
UUID=2ec2030a-5ec5-44c7-b251-a3cb78b8d853 /               ext3    errors=remount-ro 0       1
```

---

### Post by zero2xiii on 2013-08-18
Hay,

Yes you are right :).

simply add this to the fstab and reboot, issue should be resolved:

```
UUID="2ec2030a-5ec5-44c7-b251-a3cb78b8d853" /media/2TB      ext3    0   2
```

So your fstab should look like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1ebe4b97-567b-457a-bc83-40ef54677229 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73 none            swap    sw              0       0

[B]#ADDED MOUNT START
UUID="2ec2030a-5ec5-44c7-b251-a3cb78b8d853" /media/2TB      ext3    0   2
#ADDED MOUNT END[/B]

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

That should do the trick.
Remember you need to be sudo to edit the file:

```
sudo nano /etc/fstab
```
You can replace nano with your text editor of choice (gedit, geany, etc)

Cheers

---

### Post by evilbrent on 2013-08-19
Thanks, I'm sure that should be it.

Unfortunately I have a pre-existing problem with my bootup which has been giving me the error "Errors were found while checking the disk drive for /. Press F to attempt to fix the errors, I to ignore, S to skip mounting or M to manually fix". I have just been pushing I for a couple of months now (I know I know). F wasn't ever fixing the errors, but I seemed to get the machine to start working.

Now it's adding a further screen saying "Errors were found while checking the disk drive for /2_TB". So it looks like it's running into the same error, which I'm guessing was a problem with the way my fstab was in the first place...

Now it looks like I need to work out what's causing that instead of ignoring it. Thanks for your help - I'm going to call this "two steps foward one step back rather than the opposite" :-)

---

