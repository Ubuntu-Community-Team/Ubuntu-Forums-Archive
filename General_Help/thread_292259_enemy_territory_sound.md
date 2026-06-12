---
title: "enemy territory sound"
date: 2006-11-03
forum: General Help
---

### Post by stop_that on 2006-11-03
hello people, i know you have all seen these topics before about help with enemy territory sound however nothing is working

i do 
> echo "et.x86 0 0 direct" >/proc/asound/card0/pcm0p/oss

still no sound, although system sounds work fine like playing videos ect.. im using the latest edgy eft i think its 6.10 thanx  in advance

---

### Post by jongkind on 2006-11-03
Try this (from terminal):

sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

---

### Post by hexion on 2006-11-03
In dapper, I had that line (echo "et...." > /proc/..../oss) in my /etc/rc.local file, to execute it with root privileges at boot time.

Now in Edgy that doesn't work anymore.
And it's frustrating because now I have to set that command in my et_fullscreen script, and as a consecuence, it asks me for root password each time I want to play enemy territory (echoing to /proc/.../oss requires being root).

Any help on how to set that change at boot time?

---

### Post by GustavoImago on 2006-11-04
100% works
tksssss
:)

---

### Post by Haz13r on 2007-07-19
WOW THANKS. IT WORKED FOR ME TOO. Ima keep this bookmark.

---

