---
title: "No desktop icons or panel after login 14.04"
date: 2015-06-30
forum: General Help
---

### Post by linsey-young on 2015-06-30
Hi, just tried to login to my system and have been confronted with no desktop icons and no panel. The wallpaper is there, as is the pointer which responds to input, but nothing else. Anyone experienced this problem before? Any help would be appreciated.

---

### Post by ajgreeny on 2015-06-30
What happens if you rename your ~/.config/xfce4 folder as ~/.config/xfce4bak then login again.  You should get the default desktop layout and a query about default panels.

---

### Post by linsey-young on 2015-06-30
I'm getting read only file system if I try that.

---

### Post by linsey-young on 2015-06-30
> **ajgreeny said:**
> What happens if you rename your ~/.config/xfce4 folder as ~/.config/xfce4bak then login again.  You should get the default desktop layout and a query about default panels.

mv: cannot move 'xfce4' to 'xfce4bak': Read-only file system

---

### Post by rlovi on 2015-07-01
> **linsey-young said:**
> mv: cannot move 'xfce4' to 'xfce4bak': Read-only file system

Hmm, you should be the owner of that directory as it is in your home directory and thus should be read/write. Use your gui file manager to highlight the directory, right click on the directory name, click the tab on permissions and change it to read/write under owner access and try again.

Another trick that worked for me after completely messing up my desktop using compiz was to use the following command:

```
rm -r ~/.cache/sessions
```

Then logout and then log back in.

Richard

---

### Post by linsey-young on 2015-07-01
> **rlovi said:**
> Hmm, you should be the owner of that directory as it is in your home directory and thus should be read/write. Use your gui file manager to highlight the directory, right click on the directory name, click the tab on permissions and change it to read/write under owner access and try again.

Another trick that worked for me after completely messing up my desktop using compiz was to use the following command:

```
rm -r ~/.cache/sessions
```

Then logout and then log back in.

Richard

Unfortunately the GUI is not functional, as right clicking does nothing and obviously there is no panel or drop down menu. The only access I have to the system is via the recovery options in GRUB, and for some reason it is only giving me the read only file system.

---

### Post by ajgreeny on 2015-07-01
At the login screen can you hit Ctrl+Alt+F1 to get to a command line and login there with username and password (password doers not show on screen but will be entered).

At the command line prompt run command ```
ls -la .config/xfce4
``` and post what it outputs back here if you are able.
It should look a bit like
```
user@XubuntuTrusty:~$ ls -la .config/xfce4
total 56
drwxrwxr-x  8 user user 4096 Jun 17 20:00 ./
drwx------ 70 user user 4096 Jun 20 12:17 ../
drwx------  2 user user 4096 Jul  1 19:37 desktop/
drwxrwxr-x 30 user user 4096 Jul  1 22:47 panel/
drwxrwxr-x  3 user user 4096 May 26  2013 src/
drwx------  2 user user 4096 May  5 20:43 terminal/
drwxrwxr-x  3 user user 4096 May 12  2012 xfconf/
drwx------  2 user user 4096 May 12  2012 xfwm4/
-rw-rw-r--  1 user user   71 Jun 17 20:00 helpers.rc
-rw-rw-r--  1 user user   19 Jun 24  2013 help.rc
-rw-rw-r--  1 user user  281 Apr 16 23:37 xfce4-notes.gtkrc
-rw-rw-r--  1 user user  128 Apr 16 23:39 xfce4-notes.rc
-rw-rw-r--  1 user user  109 May 30 20:10 xfce4-screenshooter
-rw-rw-r--  1 user user  392 Apr  4 23:07 xfce4-taskmanager.rc
```but where this shows "user" it should show your own username.

---

