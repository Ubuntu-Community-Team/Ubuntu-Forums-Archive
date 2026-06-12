---
title: "Resolution-I must be doing something wrong"
date: 2007-04-15
forum: General Help
---

### Post by midlandman on 2007-04-15
I did some searching and it seems this is a common problem with this OS. I can't change the resolution. It's stuck on 640x480 and I'm trying to get 1024x768.
I opened a terminal and entered the command "sudo nano /etc/X11/xorg.conf" and I know I'm supposed to scroll down to "Screen" but theres no way I can do that.
At the bottom theres a bunch of commands like "Get help" and things like that with something like> pointing up and G, but no matter what I try, nothing happens.
Anyone know what I'm doing wrong? I know that when I do get to this "Screen" option I have to enter 1024x768 where ever it says "Depth".
Please help...I'm very close to going back to XP and that's the last thing I want to do! But so far it's been one problem after another with Ubuntu.

---

### Post by deanjm1963 on 2007-04-15
try using sudo gedit /etc/x11/xorg.conf instead. it will open up a gnomes text editor.

---

### Post by ubukool on 2007-04-15
My experience of Ubuntu is that it can take a bit of time at the beginning to make some things work, such as resolution and wireless internet, but I find Ubuntu a joy to use now that it's all sorted.  It's much better than XP.  Stick with it for a while longer.  You will find some very helpful people here in this community and you can also do a google search for the things you need and solve problems that way.

Don't give up just yet, some things are worth waiting for.

---

### Post by ubukool on 2007-04-15
I assume you've seen this:

[http://ubuntuforums.org/archive/index.php/t-83973.html](http://ubuntuforums.org/archive/index.php/t-83973.html)

Good luck!

---

### Post by midlandman on 2007-04-15
Thanks for the link. I printed it out and it doesn't seem to be helping much. Most of the commands I enter are not valid commands.
And when I enter sudo gedit /etc/X11/xorg.conf I keep getting "Can't open display".
After doing lots of research on this, it does seem like this is a common problem and I wonder why one of the developers hasn't come up with a patch to fix this.
I'm a raw newbie when it comes to this stuff, not like you guys that have a complete understanding of this. I read what I printed out and it makes very little sense to me, whereas you guys know exactly what it says.
I really appreciate all the help I recieved here, you guys are tops. But unless someone walks me through it in terms I understand, I'm wasting my time trying to fix this.

---

### Post by Pikestaff on 2007-04-15
Have you reconfigured xorg?

```
sudo dpkg-reconfigure xserver-xorg
```

Choose mostly defaults until you get to a part that asks what resolutions you want.  Press spacebar to choose the resolution(s) you want, and then keep going.  Once you get through, reboot.  You should now be able to choose higher resolutions.  At least, that's what worked for me.  Good luck!

---

### Post by midlandman on 2007-04-15
PIKESTAFF!!!!
You did it! It worked like a charm and if you were here in Angus Ontario I'd buy you a beer or 6.
Thanks bud, and thanks to all that had some input on this. I truly appreciate it.

---

