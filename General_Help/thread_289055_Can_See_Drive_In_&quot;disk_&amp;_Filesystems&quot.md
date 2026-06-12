---
title: "Can See Drive In &quot;disk &amp; Filesystems&quot; - Mount Question"
date: 2006-10-30
forum: General Help
---

### Post by huggy77 on 2006-10-30
I need to mount my 2nd Sata drive... I have tried a couple of different ways of doing this but i want to make sure i do it correctly because this is a production server.
 
df -h yields:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.7G   65G   4% /
varrun                506M  208K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M   76K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm

```

I can see it on the KDE Disk and Filesystems as DISK ATA st3250620ns.  What is the correct way to mount this puppy (god that sounds awful? ](*,) 

thanks!

---

### Post by MyAnda on 2006-10-30
if you want it always mounted to the same place (survive after reboot)...you will want to add an entry in /etc/fstab mounting the device (/dev/sdb1 ?) to somewhere (/home/ or whatever)...will look similar to the one you have for /

this may get you in the right direction
[http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive)

---

