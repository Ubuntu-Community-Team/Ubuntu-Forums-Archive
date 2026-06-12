---
title: "Login Issue"
date: 2007-09-05
forum: General Help
---

### Post by Spacedementia87 on 2007-09-05
Right i did a few edits to the xorg.conf and then on restart it wouldn't boot into the GUI so i had to fix the xorg.conf file in the command prompt (i had missed the S off one of the Sections)

Once that was done i booted in and could not log in.  After entering my name and password it told me that I was being immediately logged out and gave this as the details

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "bob"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
Warning: Only changing the first 7 of 11 buttons.
```

Currently logged in as a failsafe to make this post.

Oh and the files I edited were the /etc/X11/xorg.conf w whci i think i got back to how it was

I created a file called ~/.xsession and put a few lines of code in that

I edited /etc/X11/imwheel/inwheelrc which I have now put back to normal.

---

### Post by Spacedementia87 on 2007-09-05
someone must have some idea how to fix this?

---

### Post by Perfex on 2007-09-05
I have a similar problem.. no replies either, every thread I searched does not have an answer either, lots of things to try, but too no avail.. :confused:

[http://ubuntuforums.org/showthread.php?t=542842](http://ubuntuforums.org/showthread.php?t=542842)

---

