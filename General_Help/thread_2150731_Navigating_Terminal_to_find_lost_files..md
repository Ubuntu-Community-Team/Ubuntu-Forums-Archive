---
title: "Navigating Terminal to find lost files."
date: 2013-06-02
forum: General Help
---

### Post by Spency on 2013-06-02
Hi all,

I run a small home ubuntu server with amahi install on top. The computer uses an internal drive and a external connected via esata. 

Just a few moments ago I attempted to move a very large file (67gb) from one folder on one drive to another folder in the other drive - the mount points for the drives are in the same directory. I did this using terminal. Everything seemed to have gone peachily, but now I've noticed my folder is empty - at first I reason I must have somehow deleted the contents of the folder; however my web based drive analysis gui shows that there exists some very large files somewhere in my main drive (occupying 30% of all its space) while the 3tb drive sits empty. Either something is wrong with the whole system or I somehow stuck my media in an unknown location on the main internal drive. 

What's daunting for me is trying to navigate through terminal to find it.
I tried to use this code liks this, and du -sh also to try to figure it out. 
```
[COLOR=#111111][FONT=Consolas]du -hsx * | sort -rh | head -10[/FONT][/COLOR]
```

The results however shows me that my whole system is only about 3.7Gb. 

```
1.9G var1.5G    usr
363M    lib
25M    boot
8.7M    bin
7.8M    sbin
7.4M    etc
6.6M    root
1004K run
76K    home
```

All media should be stored under var, where the external drives mount point is set, and somehow there is a rogue freighter of media floating around in the linux ehter.

Please help and thanks in advance!

--
Spency

---

### Post by Habitual on 2013-06-04
> **Spency said:**
> I attempted to move a very large file (67gb) from one folder on one drive to another folder in the other drive - the mount points for the drives are in the same directory. I did this using terminal. Everything seemed to have gone peachily, but now I've noticed my folder is empty

Was it not mounted? Sounds like it.
Don't go by mount 'points', those exist even if it isn't mounted, I believe.

```
df -hT
```

---

