---
title: "usr directory has wrong permissions - change?"
date: 2008-01-09
forum: General Help
---

### Post by xenomorph99 on 2008-01-09
Hi,

I tried to copy realplayer (I knew it would screw things up) into my usr directory via midnight commander (sudo) but following the copy all the desktop icons were screwed up. I tried to reset gnome but I can't log in (just get a dialog with rubbish characters in it). I then logged in via TTY1 and can access the file system.


I see that the usr dir has permissions of drwx------

Has copying the files screwed up the usr permissions? If so, how do I change them? I tried to sudo chmod +xxx for usr in the hope of recovering it but sudo doesn't work. I tried to "su" with my logon password but that doesn't work either. Is there a way of setting usr to the right permissions? Or is the problem something else?

Cheers,
X

---

### Post by p_quarles on 2008-01-09
"sudo" isn't working because it's in /usr/bin, which apparently you don't have executable access to.

You'll have to log in in recovery mode and run this:
```
chmod 755 /usr
```
755 is the default perms setting for /usr. Be sure to look at the subdirectories (especially usr/bin, /usr/sbin and /usr/local) to make sure they have the correct permissions as well. The alphabetic permissions should look like this:
```
drwxr-xr-x
```

---

### Post by xenomorph99 on 2008-01-09
Hi,

Thanks for the swift response. I changed usr to what you said and checked the subdirs. The only folder that wasn't set as for the others was /usr/local which houses the realplayer directory that I copied so I also changed this to what you said. I can now boot into the desktop as before.

Thanks again!

X

---

