---
title: "GDebi Package Installer problems"
date: 2007-05-09
forum: General Help
---

### Post by pbbear on 2007-05-09
I have used GDebi successfully (who couldn't?) to install deb packages.

Today, I tried to use it for installing VirtualBox, a virtualization program which would allow me to control Ububtu and Windows at the same time.  It got so far, then seemed to hang up.

Worst of all, every time I try to use GDebi for another deb file, it implies that it is already running (somewhere) and won't allow a second copy to be opened.

I know there is some code to fix this problem, but I've forgotten what it is.  Anybody help?

---

### Post by zvacet on 2007-05-09
Try to install Virtual box in terminal and see after that doas Gdebi work with other apps.

---

### Post by pbbear on 2007-05-09
Thank you

I will try that.  I'm not very good at installing using the Terminal (in fact, I'm hopeless), but I'll have a go.

---

### Post by pbbear on 2007-05-09
Tried, but failed.

Could anyone guide me through installing VirtualBox from a terminal?

Address for code: [http://virtualbox.org](http://virtualbox.org)

---

### Post by pbbear on 2007-05-09
Some News on my Problem!

I found an error box which says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Can anyone tell me what to do with this; I know it relates to my problem.

---

### Post by pbbear on 2007-05-10
I was able to perform the task dpkg --configure -a  in the root terminal.  It seemed to ease the problem (the error disappeared).

Then the error showed "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

I have no idea what to do now.

---

### Post by zvacet on 2007-05-10
```
sudo apt-get remove --purge file_name
```

**file_name** is exact name of your vrtual box.This will delete virtual box.Did you install dependencies?

> You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using. 

If you didn´t do it first and after that try to install package.

---

### Post by alex_anthony on 2007-05-10
did this solve it? I have an identical problem (i think). perhaps the problem is the fact that it isn't in the repositories (hence  'I can't find an archive for it.'
the first suggestion in that last post didn't work, how do i add those libraries?

---

### Post by zvacet on 2007-05-10
[http://ubuntuforums.org/showthread.php?t=398709]("http://ubuntuforums.org/showthread.php?t=398709")

---

### Post by pbbear on 2007-05-12
Thank you both for your support and help.

In the end I took the coward's way out: I reinstalled Feisty,(groan)

However, I learned a lot in the process.  One thing I learned was to steer clear of VirtualBox!

Best Wishes

Anthony (pbbear)

---

