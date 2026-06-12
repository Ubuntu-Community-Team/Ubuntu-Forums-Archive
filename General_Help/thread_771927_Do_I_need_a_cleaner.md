---
title: "Do I need a cleaner"
date: 2008-04-28
forum: General Help
---

### Post by Bari on 2008-04-28
In XP I used CC Cleaner to get rid of all the temp files/internet rubbish etc. (surprising how much you get placed on the computer while surfing) Do I need such a thing in Linux? If not why not?

---

### Post by chewearn on 2008-04-28
1. Temp directory in linux are automatically cleared when you reboot.

2. Internet cache are handled by web browser; make the appropriate setting in the browser preferences and forgot about it.

3. Old archive files stayed in the apt cache subdir until you clean it out:
```
sudo apt-get autoclean
```

---

### Post by montamer on 2008-04-28
isn't it 
sudo apt-get clean

---

### Post by chewearn on 2008-04-28
```
sudo apt-get autoclean
```
cleans out archives from packages that are no longer installed.


```
sudo apt-get clean
```
cleans out all archives, including those of packages that are still installed.  But this is really harmful, because you can always re-download them.

---

### Post by kpkeerthi on 2008-04-28
See [Cleaning up a Ubuntu GNU/Linux system]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html"). Works for hardy too.

---

### Post by 6205 on 2008-04-28
Uhm i personally have bad feeling about gconf-editor (aka gnome registry), because there are many unused keys by removed apps.

---

### Post by Bari on 2008-04-29
Thanks for all the info, followed the link supplied by kpkeerthi and found all the info need thanks again

---

