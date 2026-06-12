---
title: "New Install Drive Space 80% used; why??"
date: 2007-07-11
forum: General Help
---

### Post by nikorc on 2007-07-11
This is a fairly new install of Ubuntu 7.10 and my root partion is using 27G of space.  I do not know where all this space has gone.  Anyone have an idea why df is saying so much is used while du doesn't show this.

```
df -h output

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G   27G  6.8G  80% /
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  132K 1014M   1% /proc/bus/usb
udev                 1014M  132K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/hdb1             184G  174G  897M 100% /media/disk-1
/dev/hda1             230G  217G  1.6G 100% /media/disk-2
/dev/sda1             459G  433G  2.3G 100% /media/disk-3

``````
sudo du -hs /* output

4.8M    /bin
27M     /boot
0       /cdrom
148K    /dev
11M     /etc
215M    /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
253M    /lib
16K     /lost+found
822G    /media
4.0K    /mnt
4.0K    /opt
0       /proc
84K     /root
6.1M    /sbin
4.0K    /srv
0       /sys
60K     /tmp
2.0G    /usr
528M    /var
0       /vmlinuz
0       /vmlinuz.old
```

---

### Post by graigsmith on 2007-07-11
check your home folder. mabey you have extra stuff in it.
even check the hidden files in your profile.  if you have been using fspot. and you have alot of photos. be aware that it makes a photo folder and makes a copy of your image in that folder, if they are big images that can take up alot of space.

---

