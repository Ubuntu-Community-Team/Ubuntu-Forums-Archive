---
title: "Mumble Push to Talk"
date: 2007-11-25
forum: General Help
---

### Post by abadtooth on 2007-11-25
Hey I'm trying to configure a push to talk key on mumble but can't get it to work, does anyone know how to use a push to talk key in mumble?
Thanks.

---

### Post by balthamaisteri on 2007-12-11
I have this same problem...

actually problem is that push to talk works, but i cannot bind any shortcuts :( 

can someone help ?

---

### Post by matthewcraig on 2007-12-11
Have you asked on their support forum?
[http://sourceforge.net/forum/forum.php?forum_id=492607](http://sourceforge.net/forum/forum.php?forum_id=492607)

---

### Post by balthamaisteri on 2007-12-11
Yeah, those forums are a mess :D

I should work in version 1.1.1, witch i am using , and i say that it is not working

---

### Post by balthamaisteri on 2007-12-15
> i had no luck with xevie too.. 
 
ls -l /dev/input/* 
 
i needed to change this devices to be accessable by my user. then there is no need for xevie to use your ptt 

> chmod usually works - but only until you do a reboot. (unless ubuntu preservers the dev files - but I don't know that). The permanent but more complex way would be to write some udev rules. 

How i can do this?

---

### Post by Shadowfire on 2007-12-16
Try the following...


**Getting the Shortcuts to work in Mumble**

You need to enable Xevie in your xorg.conf. To do this you will have to add the following line to xorg.conf, in the extensions section:

Option         "XEVIE" "Enable"

That should look something like this:

Section "Extensions"
    ...
    Option         "XEVIE" "Enable"
    ...
EndSection

Then restart the X server (Ctrol+Alt+Backspace) and try again.

---

### Post by balthamaisteri on 2007-12-17
Ive done that :<

and it did not help

theres no difference between 1.1.1 and 1.0.0.

what is the problem here :<

---

### Post by Qchan on 2008-01-17
[b][color=darkred]
I had the same issue as well! What I did was:

1) I added:

> 
Section "Extensions"

                    Option "XEVIE" "Enable"

EndSection


... at the bottom of my Xorg.conf file (gksu gedit /etc/X11/xorg.conf)
I then saved the file.

2) After that, I opened Synaptic Package Manager (System --> Administration --> Synaptic Package Manager)

3) I performed a search for xevie and checked made sure the libxevie1 was marked. 
And just encase, I marked libxcb-xevie0 and libxevie1-dbg. You can probably do this easier by typing into terminal:

> 
$> sudo apt-get install libxcb-xevie0 libxevie1-dbg libxevie1


After that, I hit CTRL + ALT and then BACKSPACE. That restarted the X server.
I logged back in and tried the shortcut again and it worked!!
[/b][/color]

---

