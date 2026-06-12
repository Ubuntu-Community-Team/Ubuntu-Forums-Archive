---
title: "Disabling automounting of Volumes"
date: 2007-06-09
forum: General Help
---

### Post by pt123 on 2007-06-09
I recently upgraded to Feisty, I have noticed that drives I intentionally didn't want mounted (i.e. not in the fstab) are being mounted as Volumes in the Computer section of Nautilius and in the File open/save dialog box of Gnome. How do I prevent this from occurring?

This type of behaviour I expect from the controlling freak nature of Windows. That is one of the reasons I liked Ubuntu.

---

### Post by pt123 on 2007-06-09
Bump, anyone?

---

### Post by eggdeng on 2007-06-09
Just a shot in the dark, but you might try including them in fstab with the noauto option?

---

### Post by pt123 on 2007-06-09
I tried using the noauto option in fstab for the partitions that I didn't want mounted and the volumes still appear. But at least now when I click on it is not asking for the admin password to mount it.

But still I need these retarded volumes off, it is becoming cluttered like Windows.

---

### Post by drs305 on 2007-06-10
I think this will do what you wanted.

Make the following directory:
```
sudo mkdir /usr/share/hal/fdi/preprobe/95userpolicy
```

Create and edit file:
```
sudo gedit /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
```

Here is what mine looks like. It hides /dev/sda1 (windows) and /dev/sda2 (system restore). To hide any particular partition, start with the device line and end with a /device line. Make sure the last line is the deviceinfo line:
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/sda1">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
<device>
<match key="block.device" string="/dev/sda2">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo> 

```

This should hide those partitions. It's not elegant but it works.

The basis of this post is mostly found at:
[http://ubuntuforums.org/showthread.php?t=428196](http://ubuntuforums.org/showthread.php?t=428196)

---

### Post by Shazaam on 2007-06-10
Or for the point and click solution (not meant to offend anyone :p)...

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

The drives are still mounted but get taken off of the desktop.

---

### Post by drs305 on 2007-06-10
> **Shazaam said:**
> Or for the point and click solution (not meant to offend anyone :p)...


The drives are still mounted but get taken off of the desktop.

That is the same as running the following line in terminal  (restore by changing to 'true'):
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

It hides them on the desktop but not in nautilus or when opening a file in gedit, which I believe is what the poster is looking for.

No offense by me, certainly :p

---

### Post by pt123 on 2007-06-10
Thanks so much **drs305**


Any idea if this has been classified as a bug or a more simpler option will be provided.

---

