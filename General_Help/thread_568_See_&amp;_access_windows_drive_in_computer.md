---
title: "See &amp; access windows drive in computer:///"
date: 2004-10-14
forum: General Help
---

### Post by wurtel on 2004-10-14
Is it possible to view &amp; access (in nautilus) another hard drive which has windows installed on it? If so, how?

I do know it's accesable from the terminal window, but I'm very uncomfortable with it, as I'm new to linux. A visual representation would be much easier.

Is there anyone that can help?

---

### Post by wurtel on 2004-10-15
*bump* Anyone...?

---

### Post by spoetnik on 2004-10-15
This is how my /ets/fstab looks:
hda1 is mijn windows drive (ntfs, read only)
hda5 is a fat drive for sharing files between windows and unbutu.
create to directories 

sudo mkdir /mnt/hda1
sudo mkdir /mnt/hda5
The icons apear on my desktop automaticly after a reboot.

# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc            /proc           proc    defaults        0       0
/dev/hda1       /windows        ntfs    ro,auto,defaults,users,umask=000 0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /data   vfat    defaults,auto,users,umask=000   0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

