---
title: "Lock.. and The mouse cursor disappears UCC.."
date: 2016-06-08
forum: General Help
---

### Post by oklokl on 2016-06-08
yakkety-alternate-amd64 2016.6.7~ 16.04 Lubuntu alternate (The same.)
[https://youtu.be/QIqbAO1TMUw](https://youtu.be/QIqbAO1TMUw)

If I lock (ctrl + alt + L) ..
The cursor has disappeared.
Exclusive graphics card was installed ... (with or without the same)


If I log out of my return to the normal mouse.

I have to log out.

So that the mouse cursor is normal.

It appears in the alternate version.

---

### Post by ajgreeny on 2016-06-08
There is at least one launchpad bug report about this problem [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604) and it suggests that you may be able to restore the cursor by switching to a text tty then back to the GUI with Ctrl+Alt+F1 followed by Ctrl+Alt+F7.

That way you will not lose any unsaved work.  I did not read all of that long bug report so you may find there is a proper solution if you dig a bit deeper, rather than just a work-around.

---

### Post by oklokl on 2016-06-08
wow.. 
My computer.
Stop function pc.
**Do not use the following bottom commands.**
YouTube live broadcast.(It occurred during viewing.)

Test several times.
But..
The same occurred.
(my pc ..)





[I][https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)
light-locker
sudo apt-get install i3lock
sudo ln -s /usr/bin/i3lock /usr/bin/slock 


sudo mkdir /etc/X11/xorg.conf.d/
echo  -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n Option  "AccelMethod" "uxa"\nEndSection' | sudo tee  /etc/X11/xorg.conf.d/20-intel.conf[/I]

---

