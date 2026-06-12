---
title: "Need help mounting my NTFS partition with NTFS-3G"
date: 2007-06-03
forum: General Help
---

### Post by Bohlio on 2007-06-03
Hello everyone :-)
 I'm trying to mount my windows partition (NTFS) with the NTFS-3G driver so i can read and write to it. On the site [www.ntfs-3g.org](www.ntfs-3g.org) It tells me to mount the partition using this command
```
mount -t ntfs-3g /dev/hda1 /mnt/windows
```

My NTFS partition is /dev/sda2, but how do i find out what the next part is? I dont know what to replace /mnt/windows with. Im kinda a noob at most Ubuntu stuff, so any help would be really great!
Thank you very much

---

### Post by taurus on 2007-06-03
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda2 /media/windows
df -h
```

---

### Post by Bohlio on 2007-06-03
Worked like a charm Taurus! Thank you very much :-)
Now I just have a few questions to further knowledge if you (or another member) don't mind :-P

What does the df -h command stand for and what is it listing?
```
chad@chad-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  2.8G   15G  16% /
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  140K  505M   1% /proc/bus/usb
udev                  506M  140K  505M   1% /dev
devshm                506M   20K  506M   1% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             968M  508M  460M  53% /media/disk-1
/dev/sda2             125G   68G   58G  55% /media/windows

```

sda5 is my Ubuntu partition, sdb1 is a flash drive i have in, and sda2 is my NTFS partition, but what does everything else stand for??
This is just for my curiousity, I want to learn all I can about ubuntu and computers in general :-P

I cant thank you enough :-)

---

### Post by strabes on 2007-06-03
I believe "df" stands for "disk free" as in free space on your disks/mounts.

If you want your ntfs partition to mount on start up, you should put the following line in your /etc/fstab: > /dev/sda2 /media/windows     ntfs-3g    defaults        0       0

---

### Post by qpieus on 2007-06-03
df is one of the many commands built into linux. Open up a terminal window and type```
man df
``` to read about the command. In case you didn't know, typing "man" followed by a command name will give you the "manual" for that command, this is called the man page. It'll say what the command does, how to use it, and what options you have when using the command. You can learn a lot from the man pages.

---

### Post by Bohlio on 2007-06-04
thank you very much everyone.
If anyone doesnt mind teaching me a little more, what do these stand for :-P...
```
 
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  140K  505M   1% /proc/bus/usb
udev                  506M  140K  505M   1% /dev
devshm                506M   20K  506M   1% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
```

---

