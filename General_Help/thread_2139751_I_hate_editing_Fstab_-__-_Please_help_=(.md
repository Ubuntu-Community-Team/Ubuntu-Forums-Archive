---
title: "I hate editing Fstab -__- Please help =("
date: 2013-04-27
forum: General Help
---

### Post by GameX2 on 2013-04-27
Hi,

I've installed Ubuntu 13.04, yesterday.  It's pretty good, except a few stuff I have to fix (Oh, and the last Nautilus is BAD. XD).
I was surprised when I realised that Pysdm was no more installable.  I only used it to automount partition from a GUI.  I know it's really old, and referred as "badly programmed" by some, but I only used it to automount my Windows partition, and never got any problem.

So now, I have to do this manually, but I always have trouble with the fstab file... -__-  I would like to be able to edit this file manually on my own, later.
Here's my current Fstab file.  After reading a tutoriel, I've added the "rw" settings myself, hoping my NTFS partitions would be readable on the next reboot, but no.  I've also added the "auto" setting, but I don't understand: the partition were mounted automatically even before that.  How, that's what I would like to know.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda9 :
UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda8 :
UUID=7BCBDD1058C5D153    /media/DATA    ntfs-3g    defaults,nls=utf8,umask=0222,user,auto,rw    0    1
#Entry for /dev/sdc1 :
UUID=D2CCB5D2CCB5B159    /media/gamex/USB_GAMEX    ntfs-3g    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda3 :
UUID=B6E88D0CE88CCC55    /media/Windows7_OS    ntfs-3g    defaults,nls=utf8,user,rw,auto,umask=0222    0    1
#Entry for /dev/sda6 :
UUID=3b44bdda-dbc7-405a-b4c2-d314939ec30d    /home    ext4    defaults    0    2
#Entry for /dev/sda7 :
UUID=417a922d-e910-48f2-853f-4ba9849edeb5    none    swap    sw    0    0

```

And here's my actual partition table:
[http://i.imgur.com/GeiNLxW.png](http://i.imgur.com/GeiNLxW.png)

I would like to automatically mount Windows7_OS and DATA, with the read, write (And execute, if possible?  I do know permissions does not exist on NTFS) permissions.  Can you help me ?

Thanks!

---

### Post by ibjsb4 on 2013-04-27
> I hate editin Fstab

Me too

[https://apps.ubuntu.com/cat/applications/pysdm/](https://apps.ubuntu.com/cat/applications/pysdm/)

---

### Post by GameX2 on 2013-04-27
> **ibjsb4 said:**
> Me too

[https://apps.ubuntu.com/cat/applications/pysdm/](https://apps.ubuntu.com/cat/applications/pysdm/)

[QUOTE="GameX2"]I was surprised when I realised that Pysdm was no more installable.[/QUOTE]

Crap. :(

---

### Post by ibjsb4 on 2013-04-27
My bad, seen the 12o4 in your distro.  :(

---

### Post by Morbius1 on 2013-04-27
> UUID=7BCBDD1058C5D153    /media/DATA    ntfs-3g    defaults,nls=utf8,umask=0222,user,auto,rw    0    1
UUID=B6E88D0CE88CCC55    /media/Windows7_OS    ntfs-3g    defaults,nls=utf8,user,rw,auto,umask=0222    0    1

In short

** get rid of all the rw,user,auto stuff
** change the umask values to 0000
** add something for windows file names restrictions

> UUID=7BCBDD1058C5D153    /media/DATA    ntfs-3g    defaults,nls=utf8,umask=0000,windows_names    0    0
UUID=B6E88D0CE88CCC55    /media/Windows7_OS    ntfs-3g    defaults,nls=utf8,umask=0000,windows_names    0    0

Assuming you actually created the /media/Data and /media/Windows7_OS  mountpoints yourself and the UUID numbers are correct it should mount as you want it.

---

### Post by Morbius1 on 2013-04-27
I thought I'd check in before I shut down for the day and I noticed something in your original post:
> but I don't understand: the partition were mounted automatically even before that.

Take these extra steps before you change fstab:

[1] Unmount the partitions:
```
sudo umount /media/DATA
sudo umount /media/Windows7_OS
```
[2] Create the mountpoints - it's not clear if you created them already or not:
```
sudo mkdir /media/DATA
sudo mkdir /media/Windows7_OS
```
Then make the changes to fstab as I suggested above.

As a final step run the following command:
```
sudo mount -a
```
It does a syntax check on your edit of fstab and then mounts the partitions with the new instructions in fstab so you don't have to do a reboot to know if it works. If everything works it will come back to the prompt if not it will give you error messages.

---

### Post by GameX2 on 2013-04-28
Thanks a bunch, this work perfectly.
I understand that I can now create/remove/rename any mount point in want (In the Media or Mnt folder).  I also go the trick with USB devices.  Now I can read and write in the directories as normal (Except the root directory of course.  Only with sudo).

What exactly does this ?

[CODE]ntfs-3g    defaults,nls=utf8,umask=0000,windows_names    0    0[\CODE]
NTFS-3G is the driver to read/write to NTFS, right?
What is the umask?  And nls=utf8 (I assume it block the usage of the ":" caracther in filenames for Windows?) ?

Last question - in my case, I would have put auto and rw to force the partition to mount automatically as read and write.  But you didn't put this - so why is this working anyways?

Thank you very much! :D

---

### Post by Mopar1973Man on 2013-04-28
I use Webmin and go to the file system and control Fstab through it.

[www.webmin.com]("http://www.webmin.com")

[ATTACH=CONFIG]241925[/ATTACH]

---

### Post by Morbius1 on 2013-04-28
>                                            UUID=7BCBDD1058C5D153    /media/DATA    ntfs-3g    defaults,nls=utf8,umask=0000,windows_names    0    0
**ntfs-3g** is the ntfs driver that enables read / write capability. ( You can also just specify ntfs since it points to ntfs-3g automatically )

**defaults** is actually a list of a whole bunch of things:
> **rw**, **suid**, **dev**, **exec**, **auto**, **nouser**, **async**, and **relatime**
The important ones are:
**rw** which allows one to read and write - maybe not to you - but it allows writing to the partition.
**auto** means that it will automatically mount at boot
**nouser** makes it so only root can mount the partition - this is as god intended. It has nothing to do with who can access it.
**windows_names** prevents you in Linux from creating a file with a name containing characters that Windows cannot interpret.

Finally **umask** - this will take a whole paragraph to explain ;)

By default an ntfs partition will mount with permissions of 777. 

Each posistion represents a different kind of user:
1st: The user who owns the mount point.
2nd: the group of users.
3rd: Others - everyone else.

The numbers have meaning:
0 - nothing
1 - execute
2 - write
4 - read

They are additive so a 7 is full access ( 1+2+4=7).

**umask** represents the permissions you want to remove from the default permissions. A umask=000 takes away nothing. Why add it at all. So you know what you've done and can easily change it if things change. For example a "umask=0222" makes the partition read only to everyone ( a 2 removes write ) . A umask=0027 will make it writeable to the owner, readable to group, and inaccessible to everyone else ( a 7 removes all permissions ).

See, I don't think using things like pysdm and the dozen or so other fstab editors is a good idea. I think templates is the way to go so when Debian or Ubuntu decide that Pysdm should be removed from the repositories ( which they have ) because of the damage it has caused over the years you are no longer dependant on it to accomplish the task.

---

### Post by GameX2 on 2013-04-28
> **Morbius1 said:**
> **ntfs-3g** is the ntfs driver that enables read / write capability. ( You can also just specify ntfs since it points to ntfs-3g automatically )

**defaults** is actually a list of a whole bunch of things:

The important ones are:
**rw** which allows one to read and write - maybe not to you - but it allows writing to the partition.
**auto** means that it will automatically mount at boot
**nouser** makes it so only root can mount the partition - this is as god intended. It has nothing to do with who can access it.
**windows_names** prevents you in Linux from creating a file with a name containing characters that Windows cannot interpret.

Finally **umask** - this will take a whole paragraph to explain ;)

By default an ntfs partition will mount with permissions of 777. 

Each posistion represents a different kind of user:
1st: The user who owns the mount point.
2nd: the group of users.
3rd: Others - everyone else.

The numbers have meaning:
0 - nothing
1 - execute
2 - write
4 - read

They are additive so a 7 is full access ( 1+2+4=7).

**umask** represents the permissions you want to remove from the default permissions. A umask=000 takes away nothing. Why add it at all. So you know what you've done and can easily change it if things change. For example a "umask=0222" makes the partition read only to everyone ( a 2 removes write ) . A umask=0027 will make it writeable to the owner, readable to group, and inaccessible to everyone else ( a 7 removes all permissions ).

See, I don't think using things like pysdm and the dozen or so other fstab editors is a good idea. I think templates is the way to go so when Debian or Ubuntu decide that Pysdm should be removed from the repositories ( which they have ) because of the damage it has caused over the years you are no longer dependant on it to accomplish the task.

Thanks! :D
Was it *that* hard to edit Fstab, when I understand ?

That's really helpful!  I will note it (I take notes of what I have trouble at first, so I can remember.  I want to become a better Linux user (No bad, but we all have flaws.  Mine are with manual GRUB settings, for example).).

Never had a problem with Pysdm personnally - I don't see which problem it'll cause if we only use it to automount a partition, but anyways.  I finally understand the fstab file, I could do it manually, now!

Thanks ! :D

---

