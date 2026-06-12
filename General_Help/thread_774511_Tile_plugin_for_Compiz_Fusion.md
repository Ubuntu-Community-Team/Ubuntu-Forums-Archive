---
title: "Tile plugin for Compiz Fusion"
date: 2008-04-29
forum: General Help
---

### Post by jsully1 on 2008-04-29
Hi all,

I've found the tile plugin to be incredibly useful, and it's unfortunate that it hasn't made it into the repositories for Hardy.  With that said though, I've gone ahead and compiled it from git for 32 bit Hardy - and you'll find it attached.  Simply extract the files and then move them to /usr/lib/compiz/ .  You may have to log out and back in or just reboot in order for the new plugin to work properly.  Please let me know if anyone has any issues!

Sully

---

### Post by al_mckin on 2008-05-03
Hey Jsully,

Thanks for posting this.  I really want tile and I dont want to compile compiz-git!

I tried your tile plugin and couldnt get it to work.
In the archive there is:

libtile.a 
libtile.la (broken symlink to ../libtile.la (?))
libtile.lai (libtool file - should this not be .la ?)
libtile.so (symlink to libtile.so.0.0)
libtile.so.0 (symlink to libtile.so.0.0)
libtile.so.0.0 (shared lib)

Does this look right?  I noticed that all other plugins have a .la, .so and .a.
So I renamed the .lai to .la and removed the broken symlink.  Also I edited the libdir to /usr/lib/compiz in the .la as it was set to /home/sully/.compiz/plugins.


After a reboot, the tile plugin appears in ccsm and I can enable it, but I dont see any config options and I dont know how to use it, assuming that I installed it correctly!

Did i mess this up? Any suggestions?

Thanks for putting this up!

Ali

---

### Post by m0nk3y_2k4 on 2008-05-04
> **al_mckin said:**
> 
...After a reboot, the tile plugin appears in ccsm and I can enable it, but I dont see any config options ...


Hey there!

I got the same problem. Anyone got an idea?

Thanks and greetings

m0nk3y

---

### Post by nottrobin on 2008-05-06
I would also like a solution to this

---

### Post by nottrobin on 2008-05-06
Yep I also tried to sort out the files to get them to work:
```
cd /usr/lib/compiz/
sudo tar -xf ~/Desktop/hartytile.tar
sudo rm libtile.so libtile.so.0 libtile.la
sudo mv libtile.so.0.0.0 libtile.so
sudo mv libtile.lai libtile.la
sudo chown root:root libtile.*
sudo chmod 644 libtile.*
```
But likewase, after all this surgery, tile appears in compiz but with no options, and whenever I try to enable it it fails (the box unticks itself again after a few seconds).

---

### Post by jsully1 on 2008-05-12
Check out my instructions for compiling it locally - I'm not sure what I'm overlooking here, sorry :/
[http://ubuntuforums.org/showthread.php?t=774561](http://ubuntuforums.org/showthread.php?t=774561)

FWIW, he's an ls -la on the target files in /usr/lib/compiz:
-rw-r--r--   1 root root 136772 2008-04-29 14:22 libtile.a
lrwxrwxrwx   1 root root     13 2008-04-29 14:11 libtile.la -> ../libtile.la
-rw-r--r--   1 root root   1023 2008-04-29 14:22 libtile.lai
lrwxrwxrwx   1 root root     16 2008-04-29 14:11 libtile.so -> libtile.so.0.0.0
-rwxr-xr-x   1 root root 131636 2008-04-29 14:22 libtile.so.0
-rwxr-xr-x   1 root root 131636 2008-04-29 14:22 libtile.so.0.0.0

---

### Post by m0nk3y_2k4 on 2008-05-14
> **jsully1 said:**
> Check out my instructions for compiling it locally - I'm not sure what I'm overlooking here, sorry :/
[http://ubuntuforums.org/showthread.php?t=774561](http://ubuntuforums.org/showthread.php?t=774561)

Hey,

I followed your instructions and.... it works! :-)

I actually can not use the "Tile Windows Vertically" and "Tile Windows Horizontally", I don't know why. But the <SHIFT><SUPER>a combination works and that's enough for me :)

Thx for this great plugin!

greetings

m0nk3y

---

### Post by jsully1 on 2008-05-14
It works for me - have you tried restarting yet?  They didn't work for me (or accept some keybindings) until after a reboot.

---

### Post by m0nk3y_2k4 on 2008-05-15
Hi,

you're right. After a reboot everything works fine. 

Thx again! Great work :-)

---

### Post by udude on 2008-08-23
I've installed the plugin as mentioned (on 8.04) and it works nicely, though I use dual-display configuration with nvidia's twinview. That introduces some window tiling-location and window-sizes bugs as my monitors do not have the same desktop size (although the same resolution). 

Those bugs aside, I'm posting here because I now experience an odd problem which seems unrelated, however started after I installed the plugin:

Relevant:
I enable "Select windows when the mouse moves over them" under System->preferences->windows.  

The problem:
The window title bar becomes grayed-out and title text disappears/reappears on window focus mouse in/out events. In more detail: moving the mouse pointer away from the window area, grays the title and hides the title text. Moving the mouse back into the window (sometimes) restores the window title-bar and its text.

The problem begun after I installed the tile plugin (manually copied the libs to /usr/lib/compiz). Even though I removed the libs later on, the magical title bar problem remains.

There's a good description of the problem +screenshot) I encounter here:

[http://www.linuxquestions.org/questions/ubuntu-63/title-bar-trouble-using-gnome-on-ubuntu-8.04-647080/](http://www.linuxquestions.org/questions/ubuntu-63/title-bar-trouble-using-gnome-on-ubuntu-8.04-647080/)

It could be completely unrelated, but this is an odd coincidence. 
Anything I could try?

](*,)

---

### Post by DaymItzJack on 2008-08-24
If you wanted to install it this way, you would of also needed to include the .xml documents located at /usr/share/compiz.

---

