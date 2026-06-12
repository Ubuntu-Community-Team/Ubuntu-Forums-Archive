---
title: "Partitions"
date: 2006-12-27
forum: General Help
---

### Post by Bider on 2006-12-27
Greetings,

Currently i embraced the new world of linux, And i was curious if i can copy files from my windows partition over to my linux partition. Which occupy on the same harddrive.
Can someone point me to the way, or run me through the process to get this done.

I'd greatly appreciate it, thankyou.

---

### Post by 23meg on 2006-12-27
Is your Windows partition recognized? Do you have icons of mounted drives on your desktop, and is the partition visible in the Computer view in Nautilus (Places / Computer)?

---

### Post by ~LoKe on 2006-12-27
You should be able to mount each partition individually (sda1, sda2, etc).

---

### Post by highneko on 2006-12-27
If you type 'df -h' maybe you will recognize it.

---

### Post by Bider on 2006-12-27
No i dont believe its visible at all. I havent found anything regarding to it.
I've searched many places.

edit: I tried that command, and it brought up the following,

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G  4.2G  9.1G  32% /
varrun                252M   48K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm

But i dont understand which should be my xp partition.

---

### Post by ~LoKe on 2006-12-27
```
sudo fdisk -l
```
See if that finds it.  The one you're looking for will use the NTFS file system.

---

### Post by Bider on 2006-12-27
Thankyou, i believe i found it as it brought up this info.

> 

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2928    23519128+   7  HPFS/NTFS
/dev/hda2            2929        4780    14876190   83  Linux
/dev/hda3            4781        4863      666697+   5  Extended
/dev/hda5            4781        4863      666666   82  Linux swap / Solaris

 

hda5 should be it possibly, as Solaris is the username for my xp account.
Thoe mounting it is what i do not know how to do.

---

### Post by ~LoKe on 2006-12-27
Nope, it's **dev/hda1 * 1 2928 23519128+ 7 HPFS/NTFS**

So,
```
sudo mkdir /media/Windows && sudo mount /dev/hda1 /media/Windows -t ntfs -o nls=utf8,umask=0222
```

---

### Post by Bider on 2006-12-27
There we go, working fine. Thankyou :)

---

### Post by ~LoKe on 2006-12-27
> **Bider said:**
> There we go, working fine. Thankyou :)

Not a problem.

---

### Post by Bider on 2006-12-27
I've mounted it with your old 'command' > sudo mkdir /media/Windows && sudo mount /dev/hda1 /media/Windows

But dident see you edited your post. So im curious if i had made a mistake mounting it,?
The mounting process worked fine, but cant access the folder because of privileges.

Even logged in as root i will recieve this message,

---

### Post by ~LoKe on 2006-12-27
Doesn't really matter.  I just edited to make it a little more precise.  Also, if you want to make your life easier and have it automatically mount everything you reboot, do this.

```
sudo gedit /etc/fstab
```
A text document will open with a bunch of crap.  Go to the very bottom and add this line:
> /dev/hda1    /media/Windows ntfs  nls=utf8,umask=0222 0    0

---

### Post by Bider on 2006-12-27
Thanks for the help, works smooth now. I can access the the partition with ease.

---

