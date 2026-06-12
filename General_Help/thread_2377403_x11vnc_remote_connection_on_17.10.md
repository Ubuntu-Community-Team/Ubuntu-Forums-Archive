---
title: "x11vnc remote connection on 17.10"
date: 2017-11-13
forum: General Help
---

### Post by seattle vic on 2017-11-13
I've updated several machines to Ubuntu 17.10, clean install and I haven't been able to get X11vnc working.  I've never set it up so it's always running (I probably should) but I ssh in to the machine and then run something like:

sudo x11vnc -forever -nomodtweak -auth /var/run/lightdm/root/:0 -display :0 -usepw

But the lightdm display manager is not installed and I can't find anything that looks like a 'magic cookie/auth file' anywhere - I've tried.

So does anybody know where to find the gdm3 auth file?  I've tried ~/.Xauthority but it doesn't work.  I've spend quite a bit of time trying to figure out how to use xauth to generate a new magic cookie file but I've found no clear instructions on how to do that.

This x11vnc magic cookie problem is vexing me; it's right up there with trying to set up a mail server :)  Any help would be appreciated!

---

