---
title: "Change Login Sound"
date: 2013-03-26
forum: General Help
---

### Post by darkwalt on 2013-03-26
Ok, so a while back, I tried to change the login sound in 10.04, and ended up getting it to not play at all.  

[http://ubuntuforums.org/showthread.php?t=1520547&page=3](http://ubuntuforums.org/showthread.php?t=1520547&page=3)

```
/usr/share/gnome/autostart/libcanberra-login-sound.desktop
``` shows that it plays a sound, but does anybody know where the login sound is located?  I have searched the forums already and have been unable to find anybody talking about this, so any help is appreciated.  Would like to get this working, preferably without having to do a workaround like I did last time.

Thx in advance

---

### Post by gifford on 2013-03-26
Here is a link to help you get the login sound in Ubuntu 12.04. [http://askubuntu.com/questions/136282/login-sound-disabled](http://askubuntu.com/questions/136282/login-sound-disabled)
You have to have it as a start up program.

---

### Post by darkwalt on 2013-03-27
Got it.  Located in /usr/share/sounds/ubuntu/stereo 

Thanks Gifford

I was actually more interested in finding out where the file is, so that way I can have it play a custom sound instead of the standard click.

Now could someone please tell me how to mark this as solved?  Can't seem to find it any more.

---

### Post by gifford on 2013-03-27
The sound used is located /usr/bin/canberra-gtk play.
But you could use any sound file by setting it up in startup applications.
Other sounds can be found at /usr/share/sounds.
Hope this helps.

---

### Post by dcstar on 2013-03-28
> **darkwalt said:**
> 
..........
Now could someone please tell me how to mark this as solved?  Can't seem to find it any more.

Read below:

---

