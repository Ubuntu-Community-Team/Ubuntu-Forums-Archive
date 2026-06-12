---
title: "how to mount partition ?"
date: 2006-08-27
forum: General Help
---

### Post by LinuxQ on 2006-08-27
I have an ext3 pasrtition ... how to mount it ?

---

### Post by amp_man on 2006-08-27
sudo mount /dev/hdX /media/hdX

replace "X" with the letter and number of the hard drive, so for the first partition on the second hard drive, it would be hdb1. You can find this info and a heck of a lot more in the ubuntu wiki (which is currently offline) or in the HOWTOs section of this forum

---

### Post by Ramses de Norre on 2006-08-27
You'll need to make a mountpoint first, this is directory in which the content of the partition will be.
```
sudo mkdir /media/name
```
Then you can choose between mounting it once or everytime on bootup,
For doing it once: ```
sudo mount -t ext3 -o nodev,nosuid /dev/hda1 /media/name
``` Replace /dev/hda1 with the actual device and partition.

For mounting everytime on bootup:
```
sudo gedit /etc/fstab
```
Add a line
```
/dev/hda1       /media/name     ext3    nodev,nosuid        0       2
```
Save and close.
```
sudo mount -a
``` will mount it immediately and that will be done on every start up too.

---

### Post by LinuxQ on 2006-08-27
Thanks, it worked :KS
but how can I change the permissions ?:confused:

---

### Post by Ramses de Norre on 2006-08-27
What are the permissions now and what do you want them to be? You should be able to just chown and chmod them.

---

### Post by maka on 2006-08-27
> **LinuxQ said:**
> Thanks, it worked :KS
but how can I change the permissions ?:confused:

chown -R <yourUserName> <directory>
chmod 755 <directory>/*

these two should do the trick:D

---

### Post by JimS on 2006-08-28
...
Ramses de Norre - Do I need to modify your code for my task below?

Task:  My notebook pc is now dual boot with XP and Dapper.
I would like to mount the XP partition so I may easily move
files from the XP NTFS partition to Dapper's ext3 partition.
I would assume that the following line needs changing.
/dev/hda1     /media/name    ext3    nodev,nosuid     0    2
Should ext3 be changed to NTFS?

Also I think I may need an NTFS to ext3 conversion program.
Anyone?

Thanks in advance for your help.
...

Being a critic is easier than being an artist.
...

---

### Post by aysiu on 2006-08-28
It would need to be ```
/dev/hda1 /media/name ntfs nls=utf8,umask=0222 0 0
```

---

### Post by JimS on 2006-08-28
...
Thanks again.
But it is not working.
Maybe I just don't know how to work it.
I can see the new partition,
which I named NTFSpart,
but not what is in it.
It appears as a blank space and
I know there is about 10gb in it.
Device manager confirms.

I didn't do Maka's chown / chmod thingy.
Is that required in my case?
I know nothing about any permissions I might have.
Just stumbling along.  Still learning from mistakes.
...

---

### Post by Ramses de Norre on 2006-08-28
Could you post the output of "sudo fdisk -l" and tell which is your ntfs partition, then also post the output of "mount".

---

### Post by JimS on 2006-08-28
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        7120    36708525   83  Linux
/dev/hda3            7121        7296     1413720    f  W95 Ext'd (LBA)
/dev/hda5            7121        7296     1413688+  82  Linux swap / Solaris

hda1 is my ntfs drive that I'm trying to see from dapper.

------------

I've got to leave for 2-3 hours.

I'm back.
...

---

### Post by maka on 2006-08-29
> **JimS said:**
> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        7120    36708525   83  Linux
/dev/hda3            7121        7296     1413720    f  W95 Ext'd (LBA)
/dev/hda5            7121        7296     1413688+  82  Linux swap / Solaris

hda1 is my ntfs drive that I'm trying to see from dapper.

------------

I've got to leave for 2-3 hours.

I'm back.
...

can you also show the results of 'mount'..
make sure the folder /media/hda1 exists, then
go to a terminal and type:
```

sudo gedit /etc/fstab

```
add this to the file:
```

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

make sure there arent any other line relating to hda1.

save the file, exit and type in the terminal:
```

sudo mount -a

```

and it should work.  if not please post the results of 'mount' when you type it in a terminal here.

---

### Post by Random Roadkill on 2006-08-31
Maybe u guys could help me with my mounting/permissions problem as i haven't had any replies to my thread in a long time...
to save me typing it al out again see this thread:
[http://www.ubuntuforums.org/showthread.php?t=211330](http://www.ubuntuforums.org/showthread.php?t=211330)

---

### Post by JimS on 2006-08-31
...
maka - you asked if folder /media/hda1 exists.
The answer is no, it does not exist
I tried to add hda1 to media while in File Browser -
no go.  Create folder is greyed out.

And after adding to fstab the hda1 line and
rebooting, I get a filesystem error.

So, it looks like I need to create /hda1 as a subfolder
to /media.  But I seem to be blocked here.
What to do??

PS: I guess I'll have to rummage thru my library
of Linux books and see if I find out how to
create the /hda1 folder via terminal.
...

---

### Post by Ramses de Norre on 2006-08-31
```
**sudo** mkdir /media/hda1
``` You need to do this as root, so you need to use sudo.

---

### Post by JimS on 2006-08-31
...
Hey gang,
Got it working on my notebook pc w/ Dapper.
(But not yet working on my old Dell w/ Breezy.)
The notebook is dual boot and the Windoz part is screwed.
But I can see the files now, so almost all is good.
I had ghosted it before installing Dapper,
so maybe I need learn to how to recover.  
Not your worry.
Thanks
...

---

