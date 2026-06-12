---
title: "cannot startx in kubuntu after hard shutdown"
date: 2008-05-10
forum: General Help
---

### Post by splitpane on 2008-05-10
I wrote a post about this a few days ago and go no response, but now have a bit more information.

When I try to log into Kubuntu, it just takes me right back to the login page.  The password is correct, however, and I can log into the console.  When I do, I try running startx and get errors, such as: 
[bunch of messages similar to the line below]
expected kysym, got XF86KbdBrightnessUp: line 72 of pc
> Error:        bad length in CompatMap
                Output file "/var/tmp/server-0.xkm" removed
Errors from xkbcomp are not fatal to the X server

waiting for X server to shut down  .FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

Then it just returns to the prompt.

This happened immediately after a hard shutdown (laptop ran out of batteries).  I'm sure something is in a bad state.  Please let me know if you have any suggestions for how to diagnose and fix.

Thanks!

---

### Post by y-lee on 2008-05-10
I would try to reinstall KDE. At the command prompt try

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

Now reboot.

```
sudo shutdown -r now
```

---

### Post by Zorael on 2008-05-10
I'm not at all sure this'll help.
```
$ sudo dpkg-reconfigure -a
```

I guess you could try something like this, too.
```
$ sudo aptitude reinstall xorg x-common x11-common xserver xserver-xorg xfree86-common
```

---

### Post by splitpane on 2008-05-10
Hello, and thanks for the quick responses.  One question I have is that I recently upgraded to heron, and during the process the upgrade crashed as it was trying to clean out the temp files.  Because of this, I am nearly out of disk space.  I am concerned that trying to reinstall kde will take more space.  Should I be concerned?  How do I delete the temp files from the upgrade?

---

