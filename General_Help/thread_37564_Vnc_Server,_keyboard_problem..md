---
title: "Vnc Server, keyboard problem."
date: 2005-05-27
forum: General Help
---

### Post by McBOeric on 2005-05-27
Bascially, when I started a Vnc server and logged into a session it asked me what keyboard settings I would like to use... (x session or gnome) and I chose gnome.

Now all the keyboard keys are mixed up and I cant find a way to change it to x session settings.

I have tried restarting/killing the process and the computer but nothing seems to work.

Any help would be appreaciated.

(btw, I didnt really know where to post this  ](*,) )

~mc

---

### Post by zepheir on 2005-08-05
I have this exact problem. After installing vncserver, then running it for the first time I was asked which keyboard settings I would like to use and I chose gnome. Now it seems that the keyboard is improperly mapped. When I hit the 'f' key it outputs and 'h', '5' produces a backspace, and so on.

Any ideas where to look to correct this issue? I've tried uninstalling and reinstalling and modifying the Keyboard settings in gnome (added a 101key setup along with the current 105 setup), as well as messing around with some options in xorg.conf. Nothing has worked yet.

---

### Post by mphetameme on 2005-08-16
I am also having this problem.

I installed vncserver, ran it, connected from work and everything seemed fine until I opened a terminal and noticed that I can't type.

I haven't found anywhere in vncserver or tightvnc viewer where I can change the keyboard mapping options or anything... 

Ugh.  ](*,)

---

### Post by trausti on 2007-12-14
I had the exact same problem. 

The problem it seems is that the keymap file gets corrupted (or set to something appropriate for gnome).

To correct this, use xmodmap to clear the settings.

Step by step: 

1) create a bash script with the following:

#!/bin/bash
echo "" > empty.keymap
xmodmap empty.keymap

2) Save this to e.g. clear_keymap.sh

chmod 755 clear_keymap.sh

3) run it:

./clear_keymap.sh


Or copy and pase the following into a terminal in your vnc session:

echo '#!/bin/bash' > clear_keymap.sh
echo 'echo "" > empty.keymap' >> clear_keymap.sh 
echo 'xmodmap empty.keymap' >> clear_keymap.sh
chmod 755 clear_keymap.sh
./clear_keymap.sh


Now kill the vnc session and start it again.

Hope that helps.

---

### Post by jarondl on 2008-01-12
I had the problem too, and it disappeard.
I've changed my .vnc/xstartup file to the one recommended by
the VNCOver SSH wiki
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

```

##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-window-manager &
{
 (gnome-panel 2> /dev/null &)
}
xterm &

```
now my VNC starts gnome without the keyboard problem. Alas, it also misses my background image. 
I have no idea why this method of starting gnome (by the use of x-window-manager, instead of gnome-session) matters.
Good Luck
Jaron

---

