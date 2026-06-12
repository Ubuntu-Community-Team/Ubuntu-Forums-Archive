---
title: "Will deleting /Media file delete other hard drives listed in it."
date: 2012-11-13
forum: General Help
---

### Post by BudworthTDog on 2012-11-13
I have a desktop with about 4 hard drives in it. My system stopped booting up and I decided I didn't want to bother fixing it as I kind of wanted to install a newer version of Ubuntu and just start clean.

I installed the new system on another hard drive. I went into the old hard drive and put all the files I wanted to keep root directory. I then deleted all the rest as I now just want to use this hard drive as storage. There is one last file "Media" that has the other hard drives listed in it. If I were to use command

 rm -r Media

Would it delete the hard drives that are listed in that file or just the "Media" file? My guess is the files in the media folder and more just "links" than the actual drives thus wont delete the contants of the listed hard drives but I figure I'd rather be safe than sorry.

---

### Post by jerome1232 on 2012-11-13
Those hard drives are mounted under /media, if you ran that command it would delete *everything* under that folder, including the data on those hard drives and leave you no way to undo it.

---

### Post by dannyboy79 on 2012-11-13
to find out if anything is "mounted" within the /media/ folder issue this command
```
mount
```

that will show you what device is mounted where. normally /media is a folder, not a file, and it contains auto-mounted removable devices like usb drives. I wouldn't suggest removing /media/ as it's a normal folder within Ubuntu.

I would definitely NOT issue rm -r /media unless you're certain that there is no partition or hard drive mounted there.

---

