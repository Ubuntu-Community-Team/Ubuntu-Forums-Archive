---
title: "Login failure, not finding files of any kind"
date: 2014-11-05
forum: General Help
---

### Post by Enin1618 on 2014-11-05
Hello, I am trying to log into my Ubuntu 14.04 GUI with the screen blacking out for a second to come back to the login screen.  I have tried all the ideas from many posts but none have worked, mainly because they all involve "apt-get install" or changing some file parameters, but these won't help me because at the root prompt "ls (or dir)" returns nothing and "apt-get install" give errors saying that "Unable to write to /var/cache/apt/" or "Unable to Parse Package List".  I have a dual boot OS system (Windows 7 and Ubuntu).   It seems that out of nowhere Ubuntu lost contact to all files.  This was not a problem yesterday, I ran Linux then Windows, going back to Linux caused this problem.  Any help is appreciated. Thank You

---

### Post by steeldriver on 2014-11-05
Hello and welcome to the forums. What do

```

parted -l

blkid

```

at the root prompt say?

---

### Post by ajgreeny on 2014-11-05
Have you tried to login to the guest session?  If that works it points to a problem with your home, probably the permissions of something in there.
Can you boot into recovery mode, or even a live DVD/USB to see what the permissions are of your **/home/username** folder.

---

