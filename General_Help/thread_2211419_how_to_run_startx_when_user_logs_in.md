---
title: "how to run startx when user logs in"
date: 2014-03-16
forum: General Help
---

### Post by duelistjp on 2014-03-16
I wanted to try seeing what I could do in terms of making a system that boots up into the google-chrome browser with no frills for personal use on an old machine i had lying around.  I used the minimal installation disk to do a command line installation and then installed xorg, alsa, chrome, and their dependencies. I made the computer autolog my user in on tty1.  I have it start chrome in the correct size on startx.  if chrome is closed out it reopens it within 5 seconds. I also got sound working after typing an extremely long command from the troubleshooting guide I found.  unfortunately I can't seem to find how to run the command startx automatically when my user logs in.  can someone help me figure it out

---

### Post by 23dornot23d on 2014-03-16
The normal place where the display manager starts up is at

/etc/X11/default-display-manager

But whether or not startx would work from there by itself  -  I do not know ........

Found this though if it helps ..........

[http://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application](http://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application)

---

### Post by duelistjp on 2014-03-16
thanks a couple posts down in there showed exactly how to do it using the .bashrc file if you are in tty1

---

### Post by 23dornot23d on 2014-03-16
Ok I see it .... thanks ..... 

I went away and looked at knoppix adriane because that seems to work on a similar principal to
what you are after ..... the disto is made for partially sighted people ...... but its very good and has what
you want in it ....... very **minimal install too based on lxde and runs from a 4 gig flash drive** .... 

The install is simple too ....... but so far I found that **knoppix version 7.0.5 works best** for me as I have nvidia graphics
and it seems to get it right for me ....... its upto version 7.2 ...... and that works better if you have monitor plugged into
the vga socket on the desktop computer / laptop ........

Got me interested now in creating something ....... 

I like dabbling with things like that ........ 

There is also a minimal type desktop called **awesome** ...... runs very few process's but is neat too.

---

