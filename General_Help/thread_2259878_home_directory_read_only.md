---
title: "home directory read only"
date: 2015-01-07
forum: General Help
---

### Post by joshrules001 on 2015-01-07
I've seen this problem before but I can't do what they say, "Check dmesg", because when I use some commands, ls, dir,dmesg, and some applications, in the terminal is closes. it's been doing this for a while now. The oddest thing is how I got it out of read only mode last time was in the bios I ran a disk check, thinking my HD may just be going bad, it passed all test btw. Does anyone know how to help. I really love linux and usually pretty good at debuging but this time I can't debug. I've even tried recovery mode it finds errors but I can't fix them. do I just need to do a reinstall? or is thier something else I can do

---

### Post by whitesmith on 2015-01-07
> **joshrules001 said:**
> I've even tried recovery mode it finds errors but I can't fix them. do I just need to do a reinstall? or is thier something else I can do

When in recovery mode you're root and should be able to fix anything. These error messages may hold the key to resolving the problem. Can you post them for us?

EDIT1: Recovery mode mounts the root partition as read-only. To fix anything you'll probably have to do```
mount -o remount,rw /
```

EDIT2: More about Recovery Mode can be found at [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode).

---

### Post by ajgreeny on 2015-01-07
It could also be worth booting to a live system and running a filesystem check on both your root and home partitions with command
```
sudo e2fsck /dev/sdx#
``` where sdx# is the sda1, sda2 or whatever they really are.

Look for any strange errors that may be found and report back here if there are any.

Have you, by any chance, been using sudo to start any GUI programs with root permissions?  I ask this, as doing so can occasionally do strange things to the permissions of /home.

---

### Post by joshrules001 on 2015-01-09
I have the slightest idea what I did but I fixed the problem. I think it was a app that was running in the background because I went into the startup apps and erased it from the start up menu. It was multibit bitcoin app.

ajgreeny no I just opened a gui in sudeo after the problem I tried to manually fix the permission problem. (no luck).

whitesmith I had done that and the problem was still there. But like I said I think it was just a startup app anyway.  because I'm on day three and it's still working right. 

thanks you two for the help.

---

