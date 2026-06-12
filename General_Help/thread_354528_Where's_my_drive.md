---
title: "Where's my drive?"
date: 2007-02-06
forum: General Help
---

### Post by icehammer on 2007-02-06
I was quite successfully running XP dualboot ubuntu for more than a month now.. Until Windows decided to screw up, as always, and i had format my drive. and reinstall. After a successful windows re-install, i installed grub successfuly. works fine now.. however, now linux doesnt show my drive on which windows is installed, although it was being shown earlier.. How do i get linux to mount /dev/hda1 (my windows drive) at each boot??

Also, the same has happened with another drive, which i simply formatted.. it was a drive which contained games. thats gone too. how do i get them back??


thanks..


PS: i'm attaching a screenshot of Gparted - /media/hda1 needs to be mounted. its the primary partition on hda.
here's the image:


[IMG]http://img223.imageshack.us/img223/5322/screenshotyg4.png[/IMG]

---

### Post by bustanil on 2007-02-06
Just add the following line to your /etc/fstab file:

/dev/hda1   /media/hda1     vfat    defaults    0   0

---

### Post by icehammer on 2007-02-06
```
# /dev/hda1
UUID=6C61-3195  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
```

the above lines already exist in /etc/fstab.. should i replace these?
please advise.

---

