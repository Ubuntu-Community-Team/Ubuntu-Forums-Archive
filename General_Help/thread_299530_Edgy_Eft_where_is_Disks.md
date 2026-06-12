---
title: "Edgy Eft: where is Disks?"
date: 2006-11-14
forum: General Help
---

### Post by juraj on 2006-11-14
I've tried out the Edgy livecd release, and had trouble reading data from my hard drives. In dapper livecd I would just go to System -> Administration -> Disks, and then just mount partitions to directories. However in Edgy that tool is missing. What should I do?

---

### Post by taurus on 2006-11-14
Open a terminal, Applications -> Accessories -> Terminal, and mount it by hand!!!

```

sudo mkdir /media/harddrive
sudo mount -t ntfs /dev/hda1 /media/harddrive
(if it's /dev/hda1 with NTFS filesystem...)

```

---

### Post by juraj on 2006-11-14
Oh, I just wanted to know if there was a GUI utility for edgy with disks-admin functionality... Because it was really handy, not just for mounting, but for viewing lots of useful info... Why did that get removed?

---

### Post by taurus on 2006-11-14
Once you've mounted it, you can use any GUI to view it with all kind of info you want.  And I don't know why they decided to remove it.  You should ask 
Canonical about it since I don't work for them and have no says in whatever they do.  However, this is a support forum and I just showed you how to mount it by hand...

---

### Post by BLTicklemonster on 2006-11-14
install pysdm and use it.

---

### Post by IanVaughan on 2006-11-22
I also really miss this tool on Edgy!

Is in not in a Dapper repository?
And if so can it not be installed from there?

(I dont know how this could be done if it is possible, but would think it was)

(I could not find this thread, and had to post [my own post]("http://www.ubuntuforums.org/showthread.php?t=304300") but it doesnt contain any good info!)

---

### Post by IanVaughan on 2006-11-22
Ok, found : [http://packages.ubuntulinux.org/]("http://packages.ubuntulinux.org/")

But the Disks "disks-admin" program does not seem to exist!

But found [This Post]("http://ubuntuforums.org/showthread.php?t=285279") very helpful.

---

