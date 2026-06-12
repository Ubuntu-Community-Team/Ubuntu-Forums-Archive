---
title: "file manager &amp; files programs"
date: 2017-10-25
forum: General Help
---

### Post by jgw on 2017-10-25
I seem to have 3 separate file managers; files, file manager, and thunar.  My problem is that neither files, or file manager, will do anything.  When I click (double) on them the little white circle comes up as if its loading and then just goes away and nothing appears.  It was working about an hour ago and then just stopped.  There was no warning, no nuthin, just stopped.  When I click on "Files" I get a list of the most recently opened files, open in new window, and "Files".  If I click on open I get the preferences for that program (but not the program).  This is a new one.  I am sure there must be a log file someplace but I have no clue as to where to find it. 

Hopefully somebody can tell me what is happening - thank you....................

---

### Post by ajgreeny on 2017-10-25
Is there a good reason for having three file managers on your system?

What happens if you open them using terminal, ie. command **nautilus** for files and **thunar**. I am not sure what the third one is so have no idea what command to suggest; have you added any that you are aware of or an added DE?

---

### Post by vasa1 on 2017-10-25
> **ajgreeny said:**
> ... have you added any that you are aware of or an added DE?
Maybe OP could post the output of
```
ls /usr/share/xsessions
```
```
env | grep XDG_CURRENT_DESKTOP
```
```
echo $DESKTOP_SESSION
```
```
lsb_release -a
```
```
uname -a
```and
```
cat /var/log/installer/media-info
```
to help people help him or her.

And, speculating from the info in the sig, * Operating System: Ubuntu 16.04.2 LTS*, OP hasn't updated the system in a while :)

---

### Post by jgw on 2017-10-29
I rebooted and the second boot did the trick and things are working again.  

thanks for the replies!

---

