---
title: "data recovery"
date: 2007-05-26
forum: General Help
---

### Post by chickenfood on 2007-05-26
my windows xp doesnt start though i am using ubuntu live cd is there a program (free,trial??
) that i can download on linux that can recover some of my data ?
i have a 2gb flash drive if that could help?

---

### Post by taurus on 2007-05-26
You just have to mount your Windows first before you can access it.  No need to install any extra to do that.  

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by chickenfood on 2007-05-26
i cant mount my hard drive due to some problem

it says 
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         876     7036438+   c  W95 FAT32 (LBA)
/dev/sda2   *        1046       30400   235788840    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdf: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         251     2015200    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)

```

---

### Post by taurus on 2007-05-26
Try

```
sudo mkdir /media/sda2 /media/sdf1
sudo mount -t ntfs /dev/sda2 /media/sda2 -o nls=utf8,umask=0222
sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
df -h
```
Now, just use nautilus and copy your personal stuff from /media/sda1 (your Windows) to /media/sdf1 (your USB drive).

p.s.  Don't forget to _unmount_ it first before you remove the flash drive.

```
sudo umount /media/sdf1
```

---

### Post by chickenfood on 2007-05-26
it comes up with this
ubuntu@ubuntu:~$ sudo mkdir /media/sda1 /media/sdf1
mkdir: cannot create directory `/media/sda1': File exists
mkdir: cannot create directory `/media/sdf1': File exists
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
mount: /dev/sdf1 already mounted or /media/sdf1 busy
mount: according to mtab, /dev/sdf1 is already mounted on /media/sdf1
ubuntu@ubuntu:~$ df -h
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by taurus on 2007-05-26
It should have been /dev/sda2, not /dev/sda1 on my part.  What's the output of this command from a terminal?

```
df -h
```

---

### Post by chickenfood on 2007-05-26
> **taurus said:**
> It should have been /dev/sda2, not /dev/sda1 on my part.  What's the output of this command from a terminal?

```
df -h
```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                502M  112K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  132K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
tmpfs                 502M  128K  502M   1% /tmp
/dev/sdf1             2.0G  243M  1.7G  13% /media/ASHISH
/dev/sdf1             2.0G  243M  1.7G  13% /media/sdf1

so whats the mistake ? im lost:(

---

### Post by taurus on 2007-05-26
These these

```
sudo umount /dev/sdf1
sudo mkdir /media/sda2
sudo mount -t ntfs /dev/sda2 /media/sda2 -o nls=utf8,umask=0222
sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by chickenfood on 2007-05-26
> **taurus said:**
> These these

```
sudo umount /dev/sdf1
sudo mkdir /media/sda2
sudo mount -t ntfs /dev/sda2 /media/sda2 -o nls=utf8,umask=0222
sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
df -h
```

this is what i got
```
ubuntu@ubuntu:~$ sudo umount /dev/sdf1
ubuntu@ubuntu:~$ sudo mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': File exists
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda2 /media/sda2 -o nls=utf8,umask=0222mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sdf1 /media/sdf1 -o iocharset=utf8,umask=000
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                502M  112K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  132K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
tmpfs                 502M  128K  502M   1% /tmp
/dev/sdf1             2.0G  243M  1.7G  13% /media/ASHISH
/dev/sdf1             2.0G  243M  1.7G  13% /media/sdf1
ubuntu@ubuntu:~$ 

```

still cant access my harddrive it says cannot mount volume

---

### Post by dbott67 on 2007-05-26
If you're still having troubles with the methods above, try this:

1. Boot your XP system using the Windows XP CD-ROM
2. Select **R** to repair/recover the installation and get to the command prompt
3. Type **fixmbr** at the prompt.
4. Reboot (and pray to the lord above!)

-Dave

---

