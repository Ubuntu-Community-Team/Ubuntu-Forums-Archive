---
title: "Quick little question"
date: 2007-07-11
forum: General Help
---

### Post by marioguy on 2007-07-11
I have installed Ubuntu on part of my hard dive and the other part is Windows(NTFS)  I can see my windows partition form Ubuntu and I would like to know if changing the name would affect anything, because I keep forgetting what sda1 is lol.

---

### Post by kevinlyfellow on 2007-07-11
You can change the name (and location ...).  What you need to do is make a directory that you want it in (/media/windows for instance).  This can be done with
```
sudo mkdir /media/windows
```

Then you need to tell the computer to where to put the partition.  To do this, you need to unmount the partition (for instance)
```
sudo umount /media/sda1
```

Then just edit the fstab file
```
gksudo gedit /etc/fstab
```

When editing the file, you will see lines like this
```
UUID=b1613f2e-11f3-4cd2-9c99-278ee957ac9d	/media/sda1	ntfs	<something>	0 0
```

The second column is where the partition is mounted.  Change that to the directory you want it in (as in the example above):
```
UUID=b1613f2e-11f3-4cd2-9c99-278ee957ac9d	/media/windows	ntfs	<something>	0 0
```

then, mount it
```

sudo mount /media/windows
```

For more information, see this site [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by mytwobears on 2007-07-11
I believe if you assign it a volume name while in Windows, when you boot into Ubuntu, it will recognize the name of the Windows partition.

For instance, I named my windows partition WINXP, so now when I boot into Ubuntu, there is a computer icon on my desktop with the name WINXP.  I double click on this to access my windows partition when necessary.

---

### Post by kevinlyfellow on 2007-07-11
> **mytwobears said:**
> I believe if you assign it a volume name while in Windows, when you boot into Ubuntu, it will recognize the name of the Windows partition.

For instance, I named my windows partition WINXP, so now when I boot into Ubuntu, there is a computer icon on my desktop with the name WINXP.  I double click on this to access my windows partition when necessary.

Yes, if you just don't like device names, you can label your filesystems, here is a howto
[http://www.debian-administration.org/articles/522](http://www.debian-administration.org/articles/522)

---

