---
title: "Mounting a hard drive with full user access"
date: 2006-07-12
forum: General Help
---

### Post by LoneIgadzra on 2006-07-12
In my pc I have a secondary 60 GB hard drive that I use for media and the like. In installing Ubuntu 6.0.6 recently, I have opted to format it as Ext3 and use [www.fs-driver.org](www.fs-driver.org) to access it in Windows. (The FAT32 4 GB file size limit could really be a problem since I use the drive for multimedia, and as a stash for large files.)

Ironically, it works better in Windows than Linux. Ubuntu mounts it as owned by root, and some other things like "noexec" that make it almost unusable, despite the contents of my fstab file,

```
/dev/hdb1 /media/hdb1 ext3 rw,user,exec 0 2
```

my mtab file still ends up showing the drive totally protected. (Unfortanately I am in Windows now and cannot copy and paste the exact line.)

I've tried mount -a, and basically every possible way to mount it with the options I want (e.g. "sudo mount -o remount,rw,user /dev/hdb1 /media/hdb1"). But nothing has any effect. It's like it's just ignoring my commands. Sure I can chmod it, but that's only a temporary fix. I want full uninhibited access to this drive for *at least* my own admin account immediately on boot.

What I am doing wrong?

---

### Post by Paerez on 2006-07-12
try:
```
/dev/hdb1 /media/hdb1 ext3 rw,user,exec,umask=0000 0 2
```
just a shot in the dim.

---

### Post by LoneIgadzra on 2006-07-12
I don't think umask is a valid option for mounting ext3 volumes, but I'll check it out next time I'm in Linux.

---

### Post by Paerez on 2006-07-12
hmm I think you're right. It is weird that the fs isn't preserving permissions. Could it be the windows ext3 mounting program that borks it?

---

### Post by RAOF on 2006-07-12
Because the filesystem supports permissions, you can just use the normal, everyday file-permission interface to change the permissions.

For example, to make everything readable/writable/(executable if it's a directory or already executable by someone), you would run:
```

sudo chmod a+rwX -R /media/hdb1

```

---

### Post by tsb on 2006-07-12
a quick solution is to input "sudo nautilus" into terminal, this will give you a super-user file browser and then go to the properties menu of the folder and enable all permissions

---

### Post by aysiu on 2006-07-13
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by LoneIgadzra on 2006-07-13
So the chmod sticks then?

---

### Post by aysiu on 2006-07-13
The *chown* sticks.

The *chmod* will stick only to the files that existed when you issues that command.

Newly created files will get the default permissions. But if you *own* those files, it won't matter.

---

### Post by xfred on 2006-07-13
Just went through this myself (new sata drive), and am kicking myself for not taking notes.  Anyhow, iirc it boils down to approximately these steps (**check these options before proceeding, I'm going from memory here (I'm at work)**):

sudo mkdir /mountpoint
sudo chown username:username /dev/hdb1
sudo chmod 744 /mountpoint

where /mountpoint is the directory you want to mount to, username is your login name, /dev/hdb1 is your harddrive (will vary - eg. for my new drive it was /dev/sda1), chown makes you the drive owner and chmod makes the directory useable.  Then add a new line to your fstab file (although looks like you've done this already) so that the new hdd is ready to be mounted, and finally run mount -a.

---

### Post by tsb on 2006-07-13
I suggest mounting in the /mnt directory.  These directories will automatically be mounted every boot AFAIK.

---

### Post by aysiu on 2006-07-13
> **tsb said:**
> I suggest mounting in the /mnt directory.  These directories will automatically be mounted every boot AFAIK. Any directory will be automatically mounted at boot as long as it's defined in the /etc/fstab file.

The mount point needn't be in /mnt or /media

---

### Post by LoneIgadzra on 2006-07-13
Awesome, everything seems to be in order now, thanks to everyone who posted!

---

