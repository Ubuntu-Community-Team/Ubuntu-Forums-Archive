---
title: "Xubuntu 14 user login via the GUI problem has returned again"
date: 2015-03-13
forum: General Help
---

### Post by garymcrobertpdx on 2015-03-13
Once again after allowing a software update, the  user login via the GUI is
screwed up!   I revisited my old tread that helped fix this before  but none
of the previous fixes worked this time.  This is becoming very tiresome and 
more than annoying.  Can some one help me sort this out one more time.

Perhaps there is a more reliable flavor of Linux other than XUbuntu?

Thanks

---

### Post by CaptainMark on 2015-03-14
I've never had this problem with Xubuntu, can you please tell us what the problem is, or at least provide a link to your old thread.

---

### Post by kerry_s on 2015-03-14
link to old thread would help, cause we have no idea what your talking about.

have you changed the log in manager or is it stock ?
your welcome to try any other flavor you wish, there all free. the next closest to xubuntu would probably be ubuntu mate. it has most of the same features as xubuntu.
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

### Post by garymcrobertpdx on 2015-03-14
Here is a link to the thread from the first and second time this happend.

[http://ubuntuforums.org/showthread.php?t=2251096&highlight=Xubuntu+14+user+login](http://ubuntuforums.org/showthread.php?t=2251096&highlight=Xubuntu+14+user+login)

---

### Post by kerry_s on 2015-03-14
so from what i'm reading you seem to have a space problem on your hd ?

```
sudo apt-get autoremove && sudo apt-get clean
```

that will clean any left over programs & any downloaded debs.

```
sudo rm -rf /var/log/*
```

clear out all log files, don't worry there created at every start. sometimes they get huge.

that should give you enough space to log in ?

---

### Post by garymcrobertpdx on 2015-03-14
Gave it a try but no luck loging in via the GUI 
I have tried to understand the &#65279;xfce4 is and how it
works its appears complicated, but I suspect it is 
involved with or the cause of this problem

Perhaps this is a clue if I do a startx after half a screen
of text I start getting a nearly endless message scroll 

Invalid MIT-MAGIC-COOKIE-1 key..

It eventually terminates  with some error messages.

---

### Post by kerry_s on 2015-03-14
you should try the ubuntu mate 14.04.2 lts, it's less complicated, less parts make up the gui, you just have caja which does the desktop, is also the file manager & mate-panel. it a fork of gnome 2 which was built to be simple from the start.

i think your xubuntu is really borked under the hood. it sounds like it's been that way for awhile.
what are your specs ? you just want to run light weight ?

---

### Post by garymcrobertpdx on 2015-03-14
I am open to trying ubuntu mate.  There are a couple of files I would
like to copy before I install.  I have a second disk in the same box.
Never copied from one disk to another via a terminal.  I assume
I will have to mount the other disk before I can do this.

---

### Post by kerry_s on 2015-03-14
just use the installer, your usb or dvd, whatever you installed with, run it live.

---

