---
title: "Good backup method?"
date: 2008-05-27
forum: General Help
---

### Post by stueng on 2008-05-27
I fiddle a lot... and I continually find myself breaking my installation, luckily Ubuntu is easy to re-install but all the customising I do to get it looking and working the way that I want takes a lot of time, and the more times I do it the more bored I get of doing it

Does anyone have a nice, easy, free (no boot up CD's please) method of snapshotting their environment incase they mess it up? I would probably need a complete snapshop as I have a habbit of breaking things quite badly (including partitions etc)

Stu

---

### Post by housam on 2008-05-27
here is what you want :

[[COLOR="Red"]_https://help.ubuntu.com/community/Backupsolutionsforlinux_[/COLOR]]("https://help.ubuntu.com/community/Backupsolutionsforlinux")

---

### Post by justleen on 2008-05-27
i wrote a how to on what to back up ... might be usefull... 

[http://ubuntuforums.org/showthread.php?t=701386](http://ubuntuforums.org/showthread.php?t=701386)

---

### Post by stueng on 2008-05-27
Good info but doesnt help me with dealing with hardware issues I have to tackle when I first install and installing of packages, building of source code etc

I want to snapshot the entire system

Your post did make me realise something though - the next time I re-install I am going to make seperate partitions for /home and /usr as this will deffinetely help

Anyone know some a good snapshot tool I can use? or maybe some kind of mirroring technique?

---

### Post by stueng on 2008-05-27
Oops I missed the first reply - thanks!

---

### Post by justleen on 2008-05-27
there is always DD or vdump to create a "snapshot" of a device/filesystem.

---

### Post by housam on 2008-05-27
> **stueng said:**
> 
Anyone know some a good snapshot tool I can use? or maybe some kind of mirroring technique?

Here
[[COLOR="Red"]_ceating disc Images using dd _[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem#head-544724647c99d68e8f9d566329ef77b5c1ffa914")

---

### Post by stueng on 2008-05-27
From what I have read so far partimage is better than DD in that it doesnt copy empty blocks. Also comes with a livecd that allows you to create DVD images from the livecd... pretty cool!

---

### Post by justleen on 2008-05-27
personally i preffer vdump..  just dump  / to a seperate partition, if everything fails, dump it back to /..

---

### Post by stueng on 2008-05-27
How would you dump it back if your operating system was messed up?

---

