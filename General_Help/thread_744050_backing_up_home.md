---
title: "backing up home"
date: 2008-04-03
forum: General Help
---

### Post by daz4126 on 2008-04-03
I'd like to make a backup copy of my home partition to an external hdd. What is the best way to do this?

I tried using the archive manager by navigation to /home and right-clicking on the 'daz' folder (my home folder that  I wanted to backup) and selected 'create archive...' I then selected home_backup.tar.bz2 and selected the external hdd as the location. Then all I get is a window saying  'getting the file list..' 

...and then the computer starts to slow down and lock up - is this normal and is there a better way?

cheers,

DAZ

---

### Post by Kevbert on 2008-04-03
Try this thread:
[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by sekinto on 2008-04-03
You could try this:

```
sudo cp -fpr /home/daz "your external hard drive directory"
```

That should copy all folders and sub folders while preserving permissions.
Although I'm not sure if it will copy hidden directories, but I know there are definitely ways to do this.

---

### Post by Tews on 2008-04-03
Kevbert is right on the money.. Quick-Start is the best way that Ive found to backup/restore Ubuntu!

[IMG]http://www.libertymanor.org/menu.png[/IMG]

---

### Post by OrangeCrate on 2008-04-03
The suggestions above are great for backing up on an external hard drive. For others reading here, who just want a simple backup method, I'll add this...

If you're using a fairly standard install, without a lot of customization, you can just drag the contents of your Home folder to a USB flash drive. Put like items into folders, then copy the folders to the stick.

Once set up, in the future when you backup, it'll update the files on the stick when you drag updated files to it. This has been my preferred backup method for some time.

If you need to reinstall sometime in the future, just drag and drop the folders back into the new Home folder. (Unfortunately, I had to do this once, but it worked flawlessly.)

---

