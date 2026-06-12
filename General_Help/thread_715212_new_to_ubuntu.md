---
title: "new to ubuntu"
date: 2008-03-04
forum: General Help
---

### Post by shawnsparks on 2008-03-04
iive never used ubuntu before and i can't figure out how to turn my javascript or any other type of media player on  i download them but they never get fully installed   please help

---

### Post by mali2297 on 2008-03-04
Open Synaptic package manager and install the packages **mozilla-mplayer**, **flashplugin-nonfree ** and **ubuntu-restricted-extras**.

For more info, see the [official docs]("https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-badformats").

---

### Post by jan quark on 2008-03-04
here are also great sites which deal with installing applications in ubuntu:

[LIST]
[*][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[*][http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[/LIST]

---

### Post by shawnsparks on 2008-03-04
thanks but when i went to system then administration then synaptic package manager then i type in my password  but the it says E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.   how do i fix it

---

### Post by bodhi.zazen on 2008-03-04
run :```
sudo dpkg --configure -a
``` in a terminal.

---

### Post by shawnsparks on 2008-03-07
i run that then it says  operation requires superuser privilege but i don't know what to do

---

### Post by PeterJS on 2008-03-07
There was a typo in Bodhi's post, it's supposed to be:
```

sudo dpkg --configure -a

```
Which will then ask you for your password. When you type your password in you will not get any visual feedback, this is normal. This will either work (hopefully), or give an error message about what failed to install properly.

---

### Post by bodhi.zazen on 2008-03-07
#-o

Fixed

---

