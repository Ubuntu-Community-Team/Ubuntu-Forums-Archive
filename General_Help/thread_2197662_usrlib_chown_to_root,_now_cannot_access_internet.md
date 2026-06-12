---
title: "/usr/lib/ chown to root, now cannot access internet"
date: 2014-01-04
forum: General Help
---

### Post by skyemoor on 2014-01-04
Ubuntu 13.04

While trying to get my Dell printer to stop throwing a 'cups insecure filter' error, I tried a number of 'fixes' in one thread dedicated to this problem.

One post ( [http://ubuntuforums.org/showthread.php?t=1313291&page=3&p=10586674#post10586674](http://ubuntuforums.org/showthread.php?t=1313291&page=3&p=10586674#post10586674) ) said the following fixed the problem;

sudo chown -hRv root /usr/lib
sudo chgrp -hRv root /usr/lib

However, I was still not able to print, so I rebooted. Upon reboot, I received a warning that said I might not be able to use Bluetooth.

Firefox came up, but could not connect to any URLs. I cannot even connect to my router. Chrome doesn't even come up. However, I am able to run Libre, for example, all of which are in /usr/lib

What do I need to do to rectify this situation?

Update: Is a reinstall my only choice? I am dual-booted, btw.

---

### Post by Impavidus on 2014-01-05
That chgrp command may have given you a problem. All files in /usr/lib should be owned by root, but not all of them belong to the group root. On my system (12.04) the exceptions (some of which may be in subdirectories of /usr/lib) are:```
drwxr-xr-x  2 root utempter     4096 okt 14  2011 utempter
-rwsr-xr-- 1 root messagebus 316824 jun 13  2013 dbus-daemon-launch-helper
-rwxr-sr-x 1 root mail 13844 jul 30 16:04 camel-lock-helper-1.2
-rwxr-sr-x 1 root utmp 13996 apr 17  2012 gnome-pty-helper
-rwxr-sr-x 1 root utmp 13996 mrt 21  2012 gnome-pty-helper
-rwxr-sr-x 1 root utmp 5364 apr 30  2011 utempter

```Fixing these may (or may not) help.

---

### Post by skyemoor on 2014-01-09
It is actually a bit worse than that, I am embarrassed to say.

I tried to quickly change back permissions, but did so in a hastily, unthoughtful manner.

I ran a chown command but accidently put in 7000 (meant to be 700) and changed all of the owners to 7000.

Now even sudo won't work. And I can't call up users-admin as "the setuid is not correct"

Is there any way to extricate myself (my daughter's laptop, actually) from this gordian knot?

---

### Post by devine.steve on 2014-01-09
You may have to boot into a live cd or usb and then mount / so you can fix this.

---

### Post by skyemoor on 2014-01-09
Thanks, devine.steve, my first Live USB gave me a "missing operating system" so I'm trying another one.

What does "mount /" mean?

---

### Post by Impavidus on 2014-01-10
chmod is usually used with numeric codes, chown usually with names. The root user has ID 0, but you only have to change a few owners – no, groups – so I don't see why all files would change ownership to the wrong owner.

You're getting close to the point where reinstalling is the fastest way out.

"mount /" means to attach the root file system of your installed Ubuntu to the directory tree of the live system. Just click on the / partition in the file manager in your live session.

---

