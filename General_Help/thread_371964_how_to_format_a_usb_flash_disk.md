---
title: "how to format a usb flash disk"
date: 2007-02-27
forum: General Help
---

### Post by fouadk on 2007-02-27
hey all

i want to format completly my usb flash disk, in windows it is a peace of cake, how to do in in ubuntu????

please help me

Thanks in advance

---

### Post by Ramses de Norre on 2007-02-27
Gparted (gnome) or QTparted (kde) are the easiest tools for this, right click the partition, unmount it, delete the current partition and create a new one.

---

### Post by fouadk on 2007-02-28
thanks alot

---

### Post by kolinab on 2007-02-28
For what it's worth, I didn't have success labelling my key with gparted. I ended up formatting it in Gparted and then relabelling it in XP of all things (egads! :)). There's got to be a better way, but for the diddling involved, this was faster. I named it "BIGKEY," because it's small on the outside, but it has a big heart.:redface:

---

### Post by bodhi.zazen on 2007-02-28
How to label :

[http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label](http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label)

---

### Post by kolinab on 2007-02-28
Hey, thanks for that - good reference there!

---

### Post by peruron on 2008-05-07
Hi there!
Sorry to bring up old topics, but the link provided brought me to a page not yet exists. I do want to know how can I rename my disk on key in Ubuntu though, so I'd appreciate any help.

Thanks

---

### Post by timcredible on 2008-05-07
i've labeled several flash drives and a couple of external usb hard drives with gparted, no problems.  i typically split up the drives as part fat32, part ext3, no problems with that either.

---

### Post by bodhi.zazen on 2008-05-07
Yes, that is an old link.

You can find this information

here : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

or here : [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by logx on 2008-05-18
Is there anybody who can clearly explain how to format an external device in Ubuntu?

I tried to fdisk /media/ but it gives me an error message

With gparted I don't see my device on the list!

---

### Post by bodhi.zazen on 2008-05-18
What file system ?

mkfs.ext3 /dev/sdb1

mkfs.vfat /dev/sdb1

---

### Post by logx on 2008-05-18
Thanks for the reply bodhi.zazen, altough I already created a new threat about this.

The problem is that my external USB device doesn't have a label yet, and when I try to create a msdos one via gparted it doesn't do anything (keeps on saying "unallocated").

---

