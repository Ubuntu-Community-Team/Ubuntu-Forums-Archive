---
title: "pcManFM super slow"
date: 2015-02-02
forum: General Help
---

### Post by kellyvotrenom on 2015-02-02
I have LXDE on an older computer and ever since I installed it PCMan has been super slow.  For an example, I have a second 1T drive that  is half loaded with music and when I access the drive it takes 5 -10 sec to show the folders.

I have always assumed that is was the old hardware, but yesterday I installed Nautilus to compare and it's fast.  Opening the music drive takes a couple of seconds.

I would install Nautilus as the default file manager, but I have seen posts that have tried this and run into problems, especially since PCMan seems to be integral to LXDE for controlling the desktop.

Any suggestions would be appreciated.

Mark Springer
industrial arts

---

### Post by Rex Bouwense on 2015-02-02
This is really odd since PCManFM is very light which is the reason it is used in LXDE systems.  It is one of the six core packages that comes with LXDE.  Something is not right since it is lighter than Nautilus.  I would try to re-install PCManFM.

---

### Post by mörgæs on 2015-02-02
Which version of PcManFM?

---

### Post by ibjsb4 on 2015-02-02
Try this in terminal.
```
apt-cache policy pcmanfm
```

---

### Post by kellyvotrenom on 2015-02-02
Here is the output from *apt-cache policy pcmanfm*:

pcmanfm:
  Installed: 1.2.0-1
  Candidate: 1.2.0-1
  Version table:
 *** 1.2.0-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status

---

### Post by mörgæs on 2015-02-03
It's a fairly recent version so I can't tell what's wrong. 
If you don't like Nautilus then what about Thunar?

---

### Post by kellyvotrenom on 2015-02-08
I tried reinstalling pcman, still slow.  

I like pcmanfm, I just don't understand why it's so slow when it is the default file manager for LXDE.

Still looking for a solution

---

