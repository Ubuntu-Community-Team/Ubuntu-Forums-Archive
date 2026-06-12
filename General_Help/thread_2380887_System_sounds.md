---
title: "System sounds"
date: 2017-12-23
forum: General Help
---

### Post by Zukaro on 2017-12-23
Anyone know if there's a way to change system sounds?  I want to enable startup sounds and change it to the Windows 95 sound, but I'd rather not edit /usr/share/sounds/ubuntu/stereo since I imagine upon updating any files I change here will get overwritten.  Plus I can't seem to get the startup sounds to play in the first place.  I can't seem to find much about this other than for login sounds (and everything I see for login sounds says to put it in a startup application, which doesn't make sense to me since I thought login sounds and system sounds in general were built in somewhere, in which case I'd be duplicating functionality by making a startup application for that).  But it's not login sounds I'm interested in.

This is on Ubuntu 17.10.

---

### Post by Dennis N on 2017-12-23
There is a dialog under Settings > Sound in Ubuntu 17.10 to change the system sound theme. These are the 'alert' sounds only. You say you want to enable 'startup sounds' and are not interested in 'login sounds'. But don't all startup sounds play when you log in (so they are the same as login sounds)? Please explain the difference.

I have in the past put a script in ~/bin to play a .wav file on log in and that works. If you need help on that, just ask.

---

### Post by speartip on 2017-12-23
If it's the startup sound you're interested in, just install sox. Then create a custom startup application, start it with the word play, then point it to the sound file you want to use.
So for eg in the command box it will be something like:
```
play /home/username/music/nameoffile
```

---

### Post by Zukaro on 2017-12-23
I remember in the past (a very very long time ago) there being a system start sound (similar to what Windows used to do when you switched on the PC); as in, before you log in after the system is ready.  I thought that functionality still existed in the OS, but I take it that's since been removed.  So I guess I'll see about running a script to play a sound as soon as the system is ready (similar to the suggestion with sox); I have a few ideas.

I'm not sure that it would work but I think if I put that command suggested by speartip into the crontab with the @reboot tag it should run at boot (although I imagine I might need to run that as root to get it to play on boot).

Thanks.  I'll play around with it a bit when I get the chance and then if I find a solution I'll post it here.

---

### Post by Dennis N on 2017-12-23
Early Ubuntu releases had some drums when the log in screen opened (and before you actually logged in), and then some fanfare when the desktop was reached. Not any more.

---

### Post by Frogs Hair on 2017-12-23
The sound is just not enabled though it can be  added to startup applications. Use any text you want in the  name and comment section.

```
 /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

---

### Post by Dennis N on 2017-12-23
Did some searching, and this explains how to play other sounds as well with canberra-gtk-play:

[http://ubuntuhandbook.org/index.php/2016/09/play-login-sound-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/09/play-login-sound-ubuntu-16-04/)

You can test and see if works in Ubuntu 17.10.

---

### Post by Zukaro on 2017-12-24
Thanks for the help

---

