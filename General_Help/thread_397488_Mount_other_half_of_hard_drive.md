---
title: "Mount other half of hard drive?"
date: 2007-03-30
forum: General Help
---

### Post by Drate on 2007-03-30
Okay, now for a slightly more intelligent question than my last blunder of stupidity....

Installed Edgy via "Resize current Hardrive" option so as to be able to dual-boot with an XP box without having to reinstall XP.  Never done that before, it was cool.  But, I notice on Dad's computer (the machine in question) there is no option under "Places" or on the desktop for "hda1", nor could I find it under the filesystem anywhere.  This has always been there automatically on my machine, which I have always reinstalled both systems on.

So yeah, how do I mount the Windows side of the hard drive?  Or Have I screwed up something major in the installation process?

---

### Post by Ramses de Norre on 2007-03-30
It's the first part, so hda1? And it's ntfs? If so: ```
sudo mkdir /media/hda1
sudo mount -t ntfs -o defaults,nls=utf8,umask=007,gid=46 /dev/hda1 /media/hda1
```

To mount it every time automatically at boot, edit /etc/fstab and add this line: ```
/dev/hda1 /media/hda1     ntfs    defaults,auto,nls=utf8,umask=007,gid=46 0       0
```

---

### Post by Drate on 2007-03-30
I assume it's the first part... I mean... windows was installed first sooo....

---

### Post by Ramses de Norre on 2007-03-30
You can check with **sudo fdisk -l**.

---

### Post by acormack on 2007-03-30
You could also do the same thing through the menus with start, system settings, disk and filesystems

---

### Post by Drate on 2007-03-30
Rockin, it works... I'll look into the fdisk and gui style mounting later... thank yall bunch!  More proof positive that Ubuntu truly has the best tech support... um... ever.

Wait a minute... start, system settings, etc?  There is no start... this is Ubuntu... I'm confused....

---

### Post by acormack on 2007-03-30
Sorry I am a kubuntu user!  

I am sure someone will point it out for you if you don't find it in the menu somewhere.

---

