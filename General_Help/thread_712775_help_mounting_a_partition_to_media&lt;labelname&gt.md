---
title: "help mounting a partition to /media/&lt;labelname&gt;"
date: 2008-03-02
forum: General Help
---

### Post by BattlePanic on 2008-03-02
In my quest to master the command line, I've just learned how to use the mount command to mount my windows xp parition by entering the following.

```
sudo mount /dev/sda1 /media
```

This will put my windows ntfs partition directly under /media.  However, I noticed that when mounting this drive by using the nautilus file manager, a subdirectory is created under /media with the windows partition's label name.  What command should I use to do the very same thing from the command line?

---

### Post by sumguy231 on 2008-03-02
You can just use:
```
sudo mkdir <folder name goes here>
```
Replacing the brackets and "folder name goes here" with the name of the folder you want. Example:
```
sudo mkdir /media/windows
```

to create a new folder, then mount it to that folder name instead of just /media.

---

### Post by BattlePanic on 2008-03-02
thanks for the reply.  I should have mentioned that I was hoping to avoid having to use mkdir.  Ideally, if there was another command or a particular switch for the mount command that would read the partition label, and make a subdirectory with that name automatically.  When I unmount the drive, it would remove the mount points directory as well.  This seems to be what nautilus does for me, but I'm not sure how I'd do it from the command line.

---

### Post by housam on 2008-03-02
Here is a good guide for mounting / unmounting windows partitions 
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/mountwindows_[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows")

---

