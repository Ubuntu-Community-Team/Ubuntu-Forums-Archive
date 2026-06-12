---
title: "kinit: no resume image found???!?!"
date: 2008-04-04
forum: General Help
---

### Post by Ed933 on 2008-04-04
Here's the problem:

When Ubuntu's booting up, right after the bar is at the end a message "knit: no resume image found" is displayed and a login shell is displayed. I can easily logon and type in "startx" and use it as normal, but the shutdown button is gone?!?!? I press logout and the display turns off, and it freezes - nothing happens, even when left on for half an hour. The only way to shut it down is buy typing in "halt now" in the console. This happens just after fixing a "can't find home directory" problem I had after shifting some partitions around. I've tried reconfiguring "xorg" but nothing happens. Also, there was another fix concerning a "system>administration>login screen" but my menu doesn't have it. 

If I have to reinstall, then I will but only as an absolute last resort. Thanks for any help:P 

Note: I'm using Ubuntu 7.10.

---

### Post by pointone on 2008-04-05
The "no resume image found" message is normal: kinit looks for an image that is created if you hibernated your system. No image was found in this case, so it boots as normal.

It sounds like GDM might not be loading on your system. When logging in at the command line, what happens if you type:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Ed933 on 2008-04-06
Hmm....it seems when I type that in it says "command not found"... 

BUT I typed in "gdm" and it said "gdm not installed"...so I apt-get'ed it and then typed in "sudo gdm restart" and the login screen worked! Now I'll restart to see if it continues. Thanks:P


EDIT: Works like a charm :D

---

### Post by pointone on 2008-04-06
If you're missing GDM, it's possible that other components of your desktop were somehow removed. To ensure a full Ubuntu GNOME installation, verify that the "ubuntu-desktop" metapackage is installed.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Ed933 on 2008-04-11
will this cancel out any of my configuration?

---

