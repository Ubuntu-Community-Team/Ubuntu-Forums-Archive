---
title: "Hiding unwanted partitions"
date: 2007-09-03
forum: General Help
---

### Post by gus_393 on 2007-09-03
I just installed 7.04 and I am dual booting with windows. 

ubuntu seems to be auto mounting a bunch of partitions that it did not do before. For example it is showing partitions such as DellUtility and my data dump (*edit*: in the "places" panel to the left in nautilus) . I know exactly what these partitions are, I just dont want them to show up.  There is no entry in my fstab for any of them and they all appear to be getting mounted to /media.

any thoughts on how i can stop these from showing up?...besides the annoyance, I want to keep the two OS`s quite seperate for several reasons.

---

### Post by bettlebrox on 2007-09-03
Comment them out of /etc/fstab

---

### Post by gus_393 on 2007-09-03
like i said in my original post, these partitions dont show up at all in my fstab and are just mounting themselves to /media....some other "smart" feature is searching them out and mounting them on the fly or something.

I`d appreciate it if anyone had any more thoughts on the subject.

---

### Post by bettlebrox on 2007-09-04
Sorry for asking this, but are you sure? On my box they are mounted and show up as:

*UUID=07D4-0B01*  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0

In recent releases, Ubunut and other Linux distro's are using UUID's instead of the actual device which can be a bit confusing.

Luck

---

### Post by gus_393 on 2007-09-04
yeah, im positive. The three i do want are present and posted with uuid`s (which i just havent bothered changing cuz it hasnt caused me problems yet). Its the whole "phantom" aspect of the problem where they are mounting without being in the fstab that is beyond me....i dont know where else the setting can be stored and delt with honestly.

---

### Post by jjross on 2007-09-04
They are being mounted as removable drives.
Look in  system/preferences/removable drives and media and look at the settings, this may be what you are looking for.
Also take look in Places/Removable Media and see if they are listed there.

---

### Post by SOULRiDER on 2007-09-04
For some reason GNOME automounts things, i dont know how to 'fix' it either. Does anyone know a solution?

---

### Post by jjross on 2007-09-04
I read somewhere on this forum that any partition that is mounted in the /media directory
will be automounted.
Try creating another directory and use it for the mount point.
Search around a bit on the forum, there are some good threads about this.

---

### Post by bettlebrox on 2007-09-05
Maybe you could specify the partitions on /etc/fstab and set them not to mount at boot time?

---

