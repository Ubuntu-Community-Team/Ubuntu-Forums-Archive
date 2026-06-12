---
title: "make read-only root filesystem for dediacted mp3/video box"
date: 2007-02-04
forum: General Help
---

### Post by nytfox on 2007-02-04
I have ubuntu server installed and customized for dedicated for mp3 and vcd/dvd player. and wonder if I can make the root filesystem readonly so that the root filesystem won't get corrupted in case of power failure or I can simply unplug the pc when I want to turn it off, similar to Livecd.  I don't want the livecd approach because it is difficult to update files when you what it to upgrade or change some files.
do you have links or howto on howto making root filesystem readonly?

my ubuntu only have the basic needed to play mp3 and VCD/DVD install
thanks

---

### Post by kingmonkey on 2007-02-04
You should have set up partitions.

Anyway: edit /etc/fstab and insert ro in your / entry:

eg:
```
/dev/hda1       /       ext3    **ro**,defaults 0       1 
```

I have no idea if ubuntu will run like this, but it wont break it because u wont be able to write to it. If you find it doesnt run then use live cd or recovery consolre to delete to ro entry from the file.

---

### Post by Ramses de Norre on 2007-02-04
That wont work, / needs to be writable... Maybe if you make separate /var and /tmp partitions but even then... You can try though, as said before it wont cause harm since / isn't writable...

---

