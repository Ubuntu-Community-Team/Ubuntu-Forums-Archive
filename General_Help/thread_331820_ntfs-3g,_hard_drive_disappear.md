---
title: "ntfs-3g, hard drive disappear"
date: 2007-01-05
forum: General Help
---

### Post by hostage on 2007-01-05
I have 2 hard drivers that i want to get read/write access to, both of them are formatted in NTFS.
When i install ntfs-3g and configure the fstab and restart the computer one of my hard drivers disappears. 

I reinstalled the OS to make the hard drive be visible, it worked! But i was very stupid cuz i could
used the "fstab.bak" to recover!

 Before i reinstalled the os i looked in GPARTED and there was a
warning triangle at the missing hard drive there it stod "input/output error" something like that!

This is my original "fstab" 
____________________________________________________________________________________________________________

# /dev/sda3
UUID=952c84bd-90c1-49ac-babc-906476375552 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0E6CD7F26CD7D297 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=10140E02140DEC12 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1

_____________________________________________________________________________________________________________

This is how i do to configure it, the bold is the text i have changed. 
_____________________________________________________________________________________________________________

# /dev/sda3
UUID=952c84bd-90c1-49ac-babc-906476375552 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0E6CD7F26CD7D297 /media/sda5     **ntfs-3g**    defaults,**locale**=utf8,umask=007,gid=46 0       **0**
# /dev/sdb5
UUID=10140E02140DEC12 /media/sdb5     **ntfs-3g**     defaults,**locale**=utf8,umask=007,gid=46 0      ** 0**
# /dev/sda1
______________________________________________________________________________________________________________

The problem is that my " SDA5 " hard driver disappears! but the " SDB5 " work perfectly.
I want the other to be visible.

Someone know how to make the second hard driver to be visible? please HELP
im a linux newbie. 

i use **ubuntu edgy **

---

### Post by xiaoxin on 2007-01-05
you mean sda5 dissapears?

---

### Post by hostage on 2007-01-05
yes "sda5" disappears!  ooh i see i wroted wrong before.. well yes.. SDA5 disappears

---

### Post by xiaoxin on 2007-01-05
can you be more specific? it dissapeared where?
it wasn't mounted?

---

