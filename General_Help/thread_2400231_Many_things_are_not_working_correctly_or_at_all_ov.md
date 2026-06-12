---
title: "Many things are not working correctly or at all over VNC"
date: 2018-09-04
forum: General Help
---

### Post by bsh on 2018-09-04
Hey,
I'm running a few headless machines, using VNC if I need the desktop. I've been running xubuntu 16.04, things weren't perfect on it either, but now since I upgraded to 18.04 a few days ago, things gotten even worse.
What do I mean: for example, the upgrade itself: when update manager runs on the desktop, it works fine, updates and stuf, but then it shows me [this]("https://www.omgubuntu.co.uk/wp-content/uploads/2016/04/1404-lts-to-1604-lts.jpg") window (edit: picture is not mine, just some example from the internet), and I click on Upgrade... it disappears and nothing happens. I have to run update manager from a terminal as root to make it work.
Now on 18.04, I can't run thunar as root from a desktop launcher icon, nor can I start xterm launching a script as root.
On 16.04 I was using gksu for that which worked perfectly fine, wether on VNC or on the actual screen :0 (one machine has a display on it though not used much)
And the supposedly working and recommended solutions for replacing gksu, for example running it with pkexec don't work either. If I start thunar with pkexec from a terminal, then it does work, but not from a desktop launcher. It doesn't display the authentication window or anything at all. Same for xterm. However, when I try to run xterm from a terminal, it does say why it is not running: it complains about the display variable not set - but it IS set, and correctly to display :1 which is the vnc session. Even if I specifically tell it to use :1 via a command line, it still doesn't work with the same complain.
Some of this does work though, when I login locally to the :0 screen.
Other stuff that needs admin priviliges and wants me to authenticate do work, for example, gparted or synaptic, those work correctly, showing the authentication dialog, etc. Those have polkit rules I guess.
Maybe my vnc session is not set up correctly (althoug it seems to be alright to me), or some of this stuff (pkexec?) has been hardcoded to use display :0 and fails? I have no idea.
Any help is much appreciated.

---

### Post by ajgreeny on 2018-09-04
Can you confirm the version you did have and the version you are using now as the image you show suggests that you may have started with 14.04, not 16.04 as you said.

You can not run an upgrade from 14.04 to 18.04 in a single operation but would have to do it in two steps, 14.04 to 16.04, then 16.04 to 18.04 so please show us the output of ```
lsb_release -a
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by HermanAB on 2018-09-04
Note that VNC is mostly a Windows thing.  If both machines are Linux based, then you should use SSH:
$ ssh -X user@server "gedit filename"

The local machine already has a desktop, so there is no point in overwriting the local desktop with a remote desktop.

---

### Post by bsh on 2018-09-04
it's not my image (obviously it's gnome and not xfce...), i just found it on the internet so you know what i'm talking about.

---

