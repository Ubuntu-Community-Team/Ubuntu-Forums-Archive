---
title: "Permissions change themselves after being logged in for a few minutes!"
date: 2013-03-20
forum: General Help
---

### Post by dunkuk on 2013-03-20
Well this is odd,
I'm using 12.04 quite happily, all up to date.  Amule started to tell me it could not access folders to download files to.  Then Firefox tells me it can not open as it is already running.  After a lot of messing about I realised it is not just amule and firefox, after logging on to the system I can modify or change files for about 1-2 minutes.  And successfully open Firefox, after about 2 minutes without doing anything other than browsing the web or opening and closing system manager all my permissions seem to change so I can not delete anything, and a lot of software wont open if it relies on having write access.

By restarting the system I get another minute or two to run checks and delete files then have to reboot to do any more!

Any ideas or things to check first?

I've deleted some files to make sure there is room so I have not run out of disk space (although I may have done when the problem started), tried running fix packages in synaptic and run autoclean.  Is there a way of fixing things without having to do a reinstall?

Thanks

---

### Post by redmk2 on 2013-03-20
Are you running a LiveCD version of Ubuntu?  Are you logged in as the user that installed the system?  What do you get from the terminal (Cntl-Alt-t) with this command ```
ls -l
```

---

### Post by dunkuk on 2013-03-21
Hi,
Well after leaving it overnight in suspend it seems to be back to normal. I guess it can't be the action of leaving it in suspend that fixed it!  I'm not going to try anything during the day as I need to use it for work, I'll try a reboot tonight and see what happens.

That command will be very handy I can see how i could use it to compare permissions with a working and non working system.  I'll post below what it returns at the moment with a "working" system.

duncan@duncanubuntu:~$ ls -l
total 52
drwxr-xr-x  2 duncan duncan 4096 Mar 20 21:23 Desktop
drwxr-xr-x 10 duncan duncan 4096 Mar 14 18:33 Documents
drwxr-xr-x  3 duncan duncan 4096 Mar 20 21:35 Downloads
-rw-r--r--  1 duncan duncan 8445 Oct 30 01:23 examples.desktop
drwxr-xr-x  2 duncan duncan 4096 Oct 30 01:28 Music
drwxr-xr-x  2 duncan duncan 4096 Oct 30 01:28 Pictures
drwxr-xr-x  2 duncan duncan 4096 Oct 30 01:28 Public
drwxrwxr-x  3 duncan duncan 4096 Dec 21 15:22 Stonehenge 2012
drwxr-xr-x  2 duncan duncan 4096 Oct 30 01:28 Templates
drwxrwxr-x  4 duncan duncan 4096 Dec 30 16:07 Ubuntu One
drwxr-xr-x  2 duncan duncan 4096 Mar 20 21:35 Videos

---

### Post by 3rdalbum on 2013-03-21
It sounds like you have major filesystem damage. When the system detects the damage it remounts the disk as read-only.

You need to run an fsck from a live CD to fix the damage. If it does no lasting good, your disk may be failing, or you might just need to format the disk and reinstall.

---

