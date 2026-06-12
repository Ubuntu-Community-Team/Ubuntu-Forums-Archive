---
title: "For the love of baked beans why can't I flippin delete this directory."
date: 2007-01-30
forum: General Help
---

### Post by Roasted on 2007-01-30
Long story short, something is terribly wrong with my file system. I've got 3 drives. SDA1, SDB2, and this IDE drive.

Somehow there are 2 folders that the IDE drive pops up in, HDD and HDC1. I renamed HDC1 to "trash". Now I'm trying to delete it and re-make the directory. I deleted HDD, but HDC1 which is now named trash I cannot delete.

It says it is not empty.

When I right click and go to properties, it says contents: nothing.

The folder is empty. Yet when I try to delete using sudo rmdir trash, it just refuses to delete it. I just want to get rid of this, create a new folder (hdd1) so I can mount my IDE drive and sync over my home folder.

Also, why would the folder "trash" only recognize 123 gig on the drive, when it's a 189 gig drive? It's formatted with EXT3.

---

### Post by auroraborealis on 2007-01-30
Have you tried "sudo rm -rf trash"?

---

### Post by Roasted on 2007-01-30
Oh wow...

The type of font that was on the page where I saw "rm-rf" didn't appear to have a space there. This time when you posted that, there was an obvious space.

Thank you. So very much...

---

### Post by Roasted on 2007-01-30
How's about a new question while I'm on the topic of mounting folders to the right location.

I just got rid of trash (hdc1) and hdd. Now I'm starting off fresh. I want to create a new hdd folder in /media and mount my IDE drive to it.

Here's what I got.





jason@jason:~$ cd /media
jason@jason:/media$ sudo mkdir hdd
jason@jason:/media$ cd ~
jason@jason:~$ sudo mount /dev/hdd /media/hdd
mount: you must specify the filesystem type
jason@jason:~$


How can I specify a file system type?

---

### Post by Roasted on 2007-01-30
edit - My mistake. Ignore this.

---

### Post by mbeierl on 2007-01-30
```
sudo mount -t ext3 /dev/hdd /media/hdd

```

---

### Post by Roasted on 2007-01-30
Okay. Everything is squared away now. But my 189 gig drive, when I right click and go to properties, it says it has 177 gig usable.

Why?

---

### Post by po0f on 2007-01-30
Roasted,

~5% is reserved for the super-user/root, meaning you can't use it.  Also, there is a little overhead when running a journaling filesystem (ie, ext3, reiserfs, etc).

---

### Post by Roasted on 2007-01-30
Thanks for the tip bud! I didn't realize that. I guess Windows does this too, but Windows just doesn't reserve it until it's used, right?

---

