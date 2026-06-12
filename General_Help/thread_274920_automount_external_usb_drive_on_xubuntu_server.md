---
title: "automount external usb drive on xubuntu server"
date: 2006-10-10
forum: General Help
---

### Post by mmoalem on 2006-10-10
hi there all - been searching high and low and also there are many posts about automounting i couldnt make them work for me so here is my problem...:)
first my setup - i have a headless old laptop running xubuntu as file/print server. i have webmin, vnc and ssh for remote control. I have an external philips usb HD that has 2 partitions formated to fat32. when loged in to xubuntu's xfce the partitions show on the desktop as PHILIPS1 and PHILPS2 and clicking on them mount them automaticly. however prior to logging in and manually mounting them them they aren't mounted and so not accessible. I have tried to follow on the instructions on this page ([http://linux.wordpress.com/2006/10/07/suse-automatically-mount-usb-hard-drives/](http://linux.wordpress.com/2006/10/07/suse-automatically-mount-usb-hard-drives/) i know its suse but being a newbie thought it worth a go)
but it didnt work at all
so back to square one and request for help...
cheers
michel

---

### Post by dannyboy79 on 2006-10-10
check this out, this may be it., i know your drive probably isn't a flash drive but i don't think that matters cause the kernel uses the hotplug module.
[http://howtos.linux.com/howtos/Flash-Memory-HOWTO/linux-2.6.shtml#hotplug](http://howtos.linux.com/howtos/Flash-Memory-HOWTO/linux-2.6.shtml#hotplug)

---

### Post by mmoalem on 2006-10-11
thanks for the suggestion but it didnt work for me. in fact 'systool  -vb scsi | grep vendor '(taken from the page you suggested) doesnt show the philps hd at all.
so still looking for solutions...
cheers
michel

---

### Post by mmoalem on 2006-10-11
hi there again - appologies for the prvious post as i have gone over the process in the suggested page again and finally worked it out. now i can mount everything with *sudo mount -a* without logging into x
however now i need to run *mount -a* on startup rather than manually...
any suggestions?

---

### Post by dannyboy79 on 2006-10-11
> **mmoalem said:**
> hi there again - appologies for the prvious post as i have gone over the process in the suggested page again and finally worked it out. now i can mount everything with *sudo mount -a* without logging into x
however now i need to run *mount -a* on startup rather than manually...
any suggestions?

Well something isn't right, the system does a mountall when it boots up, since you do a sudo mount -a i know that what is being mounted is everything within fstab so I am not sure why your drives aren't being mounting upon bootup? other than that I am not sure. well doesn't like a server start certain services like ssh or ftp etc etc. couldn't you create a script or something so that it would be run by the system upon bootup? can't help you anymore.

---

### Post by mmoalem on 2006-10-11
finally it is working and all seems well (at least it seems like that at this late hour of the night)
anyway for anyone conserned this is how i did it:

1. *systool -vb scsi | grep vendor*

get vendor id - in my case HDT72252

2. [I]sudo nano /etc/udev/rules.d/z90-philips.rules

# external HD 1
BUS="scsi", SYSFS_vendor="HDT72252*", NAME="PHILIPS%n"", run+="/bin/mount -a"[/I]

3.[I]sudo nano /etc/fstab

/dev/PHILIPS1   /media/PHILIPS1 vfat,ext2  user,auto,rw  0 0
/dev/PHILIPS2   /media/PHILIPS2 vfat,ext2  user,auto,rw  0 0[/I]

thanks again for the earlier suggestion it put me on the right track and all was missing was to add ", run+="/bin/mount -a" to the rules file

---

### Post by dannyboy79 on 2006-10-13
> **mmoalem said:**
> finally it is working and all seems well (at least it seems like that at this late hour of the night)
anyway for anyone conserned this is how i did it:

1. *systool -vb scsi | grep vendor*

get vendor id - in my case HDT72252

2. [I]sudo nano /etc/udev/rules.d/z90-philips.rules

# external HD 1
BUS="scsi", SYSFS_vendor="HDT72252*", NAME="PHILIPS%n"", run+="/bin/mount -a"[/I]

3.[I]sudo nano /etc/fstab


/dev/PHILIPS1   /media/PHILIPS1 vfat,ext2  user,auto,rw  0 0
/dev/PHILIPS2   /media/PHILIPS2 vfat,ext2  user,auto,rw  0 0[/I]

thanks again for the earlier suggestion it put me on the right track and all was missing was to add ", run+="/bin/mount -a" to the rules file

are you saying that the link i posted along with what you also pointed out is what made it work? I am glad if that's the case, I enjoy helping people, even though all I did was go to gogle and search, quickly read the forum, thought it matched your question to the tee and let you know where to go to figure it out. Chalk another 1 up for dannyboy. dannyboy is here to save the day. HA HA

---

