---
title: "slow starting videoplayer"
date: 2005-04-10
forum: General Help
---

### Post by mr.tulo on 2005-04-10
lately when i try to start my favorite media player vlc, it takes a long, long time for the window pop up. also totem behaves like this. i tried reinstalling through synaptic but without any luck...

this is how the story goes;

---
 moi@ubuntu:~ $ vlc
VLC media player 0.8.1 Janus
libhal.c 767 : org.freedesktop.DBus.Error.NoReply raised
"No reply within specified time"

 moi@ubuntu:~ $ totem
libhal.c 2282 : Error sending msg: No reply within specified time

(totem:9799): GLib-GObject-WARNING **: gsignal.c:1716: signal `got-redirect' is invalid for instance `0x8336d88'
 moi@ubuntu:~ $
---

i guess this libhal.c thing is messed up, but how do i fix it?

---

### Post by Calvin on 2005-04-19
I actually have exactly the same problem, at least with Totem (I haven't installed VLC, so I don't know about it). Another thing maybe worth mentionning is that I'm using the totem-xine version of Totem, not totem-gstreamer.

I have the same error message:
libhal.c 2282 : Error sending msg: No reply within specified time

Any idea on how to to resolve this bug?

---

### Post by bjunix on 2005-05-02
same problem here... 
nobody hasn an idea?

---

### Post by bjunix on 2005-05-04
i tried starting vlc with xfce and there are no problems. start up is quick and no error messages..

so it has to be a problem with gnome.

---

### Post by bjunix on 2005-05-04
ok i found something related to this. 

[http://ubuntuforums.org/showthread.php?t=27087](http://ubuntuforums.org/showthread.php?t=27087) 

seems to be a problem with dbus. after i restart /etc/init.d/dbus-1 vlc start up quickly as it should.

---

