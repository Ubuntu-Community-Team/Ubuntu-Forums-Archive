---
title: "Can't get windows partition /etc/fstab entry to work, plesae help"
date: 2007-12-12
forum: General Help
---

### Post by bitter_mike on 2007-12-12
Edit: just noticed the spelling error. My bad.

Hey all,
This is my first time back in linux in the past 6 or 7 years (decided to strop drinking the MS coolaid 7 days ago), so bear with me a bit.

I'm running Gutsy on my Dell Inspiron E1505 and I've having some issues getting the windows partition to mount when the computer boots. When I installed, the ntfs partition had no entry in /etc/fstab. But, conveniently,t when I try and mount the partition with the GUI, it mounts no problem (after asking me for my root pw). I can read and write to the drive and do all those marvelous things you coudn't do six years ago. When I mount it in this way, this is what its /etc/mtab entry looks like:

/dev/sda2 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

Looks good to me, but I want this partition to mount at start. So I figure I have to make an entry is /etc/fstab for it. So I did, with exactly those same flags (except a different mount point) to see if I could mount it then. The /etc/fstab entry looks like this:

/dev/sda2  /media/win  fuseblk    rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

When I try and use the GUI to mount that, I get this error message: "You are not privledged to mount this volume."

So I tried adding the user flag to the front of those options, and when I try and mount that, I get this different error message: "Invalid mount option when attempting to mount the volume."

Once I get this working, I imagine the next step is to add auto to the options so it mounts on startup, but I can't do that until I'm sure I can mount and unmount the partition once I've booted. Anyone know why I'm getting those errors? Any help would be most appreciated.

---

### Post by lswest on 2007-12-12
i believe that entry doesn't work in fstab, you'd have to take an entry from an fstab and edit a copy of that entry for your drive.  I'd paste mine, but i have to re-install gutsy (Paragon Partition Manager corrupted the ext3 filesystem when i tried to resize it, instead of doing the right thing and doing it in GParted:P impatience is the 8th deadly sin:P lol)

---

### Post by bitter_mike on 2007-12-12
Hmmm...strange. I figured they 'd be the same. Does anyone have an example from their own /etc/fstab? That'd be great.

---

### Post by bodhi.zazen on 2007-12-12
> /dev/sda1 /media/windows ntfs-3g users,uid=1000,gid=100,umask=007 0 0

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by logos34 on 2007-12-12
that mtab/mount line won't work in fstab

try using the ntfs-3g config gui--it will edit fstab for you.  So take out that line and then

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support

reboot

---

### Post by bitter_mike on 2007-12-12
Did some more looking, and now I have this in my /etc/fstab for my ntfs partition:

/dev/sda2 /media/win ntfs-3g user,rw,nosuid,nodev,noatime,auto 0 0

I can do a "sudo mount /media/win" and it mounts perfectly. But when I mount it through the GUI, instead of asking for my root pw, it just says permission denied. This setup would be perfect if I could get it to do that. Any ideas on that front?

---

### Post by bitter_mike on 2007-12-12
> **logos34 said:**
> that mtab/mount line won't work in fstab

try using the ntfs-3g config gui--it will edit fstab for you.  So take out that line and then

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support

reboot

Did that, it worked great for the automatically mounting at boot (thanks a bunch, logos), but once I booted, I couldn't unmount the drive (permission denied from the gui). I added "users" to the flags in fstab and now I can unmount the drive, but not mount it again. If I try and mount it again (either in GUI or from the command line) I get this:

Error opening partition device: Permission denied
Failed to mount '/dev/sda2': Permission denied

The fstab entry for the disk looks like this:

/dev/sda2 /media/windows ntfs-3g users,defaults,locale=en_US.UTF-8 0 0

Is there a separate permissions change I need to make to mount the drive? Or at least a way to make the GUI ask for my root password so it can do it with root permissions from the GUI?

---

### Post by logos34 on 2007-12-12
So, on the command line are you trying

sudo mount -t ntfs-3g /dev/sda2 /media/windows

and it gives 'Permission denied' ?

---

### Post by logos34 on 2007-12-12
I don't use the option 'users' in mine and I can un- and remount at will.  take it out and try it

mine:
> # Entry for /dev/hda1 :
UUID=B6D4F08CD4F04FDB /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by bitter_mike on 2007-12-12
> **logos34 said:**
> So, on the command line are you trying

sudo mount -t ntfs-3g /dev/sda2 /media/windows

and it gives 'Permission denied' ?


No, thats the error message I get when I try to do it without sudo. When I do it with sudo, it works just fine. I want it to either work w/o sudo (i.e. let my normal user mount and unmount the filesystem) or alternatively, if I try to mount/unmount via the GUI, instead of telling me "Permission Denied" I want it to ask me for my root password, which is what it does if you try to mount it when there's no fstab entry for it.

---

### Post by bodhi.zazen on 2007-12-12
Two ideas :

1. Check your fstab options, I am not sure all of the ones you are using are valid for ntfs filesystems.

2. Log out and back in , often you need to do that to update gui tools (menus, etc).

---

### Post by bitter_mike on 2007-12-13
> **bodhi.zazen said:**
> Two ideas :

1. Check your fstab options, I am not sure all of the ones you are using are valid for ntfs filesystems.

2. Log out and back in , often you need to do that to update gui tools (menus, etc).

1. All the options in there, with the exception of the "users" flag are now the one's automatically provided for when using ntfs-config. Plus the device mounts successfully at boot and when using sudo from the terminal, so I think the options are ok.

2. Gave it a shot, no dice.

---

