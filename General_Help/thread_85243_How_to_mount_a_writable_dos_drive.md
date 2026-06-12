---
title: "How to mount a writable dos drive?"
date: 2005-11-02
forum: General Help
---

### Post by Zingam on 2005-11-02
My fstab entry is:

/dev/hda10      /mnt/dos        vfat    rw,users,auto       0       0

The dos drive is mounted but I cannot write to it as an ordinary user. What do I miss here?

The gnome disk mounter applet I use in hoary used to display the size of the disk partitions, now it doesn't. Can I make it show it again?

:) Last question: can I mount a device to multiple directories at the same time for example
/mnt/dos
/media/hda10

---

### Post by jatos on 2005-11-02
Try writing to it as root ;-) 

A problem with the Linux permissions is DOS volumes can normally only be accessed as root, I find that the linux permissions take security *too* far.

---

### Post by RAOF on 2005-11-02
Looks like you missed a ",umask=0000" after the "auto".  See [this wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29").

AFAIK, there's nothing stopping you mounting the same device at 2 different mount points.  Why not try!

---

### Post by Zingam on 2005-11-03
Now my fstab entry is:
/dev/hda10      /mnt/dos        vfat    user,auto,fmask=0111,dmask=0000       0       0

I can write files but I cannot delete them with Nautilus. When I move them to Trash, they do not appear in it and they are not deleted. When I open the drive in Windows, I can see a folder .Trash and all files are in there.

So what's wrong now? I had no problem doing that in Hoary!

---

### Post by justinjstark on 2005-11-08
I just did this and it works for me.  I can delete in nautilus and everything.

/dev/hda5       /media/hda6     vfat    auto,user,fmask=0111,dmask=0000 0 0

I don't think switching auto and user would make a difference but it might be worth a try!?!??

---

