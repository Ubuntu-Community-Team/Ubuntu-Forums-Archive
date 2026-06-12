---
title: "VNC (Windows into Xubuntu)"
date: 2007-02-15
forum: General Help
---

### Post by chris.snafu on 2007-02-15
I searched the forums, found some things that kind of pointed me in the right direction, but not completely.

i am working on getting a linux "home server" per-se up and running, but i want to be able to have it off in a corner where it wont be bothered and our of the way, but if i need to work on it quick, not enough of something to need a monitor, keyboard and mouse, to be able to do it from my desktop, which is winXP (im sorry, im a heavy gamer, and thus, need it)

(comp specs in sig)

if you know of a way to do this, please point me in the right direction.

i dont know if i need this ssh thing, or if VNC, such as [http://www.tightvnc.com]("tight VNC") will get the job done, and as a linux noob, i dont know how to get it working.

i didnt find anyone in the same predicament as i am, windows to linux, only linux to windows or linux to linux.

thanks for the help in advance.

---

### Post by mr_mop on 2007-02-15
I am assuming that as its a server, you've installed a server version and so don't have a GUI.  If this is the case then SSH is the way to go.
Try installing PuTTY on your XP box:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
You can then SSH into your linux box.  You may need to use`

If you installed a desktop version of ubuntu, then VNC is the way to go.
Install x11vnc on your linux box.  Then you'll need a VNC client on your XP box.
[http://www.realvnc.com/](http://www.realvnc.com/) This is the one I use.

---

### Post by chris.snafu on 2007-02-15
Im using the desktop version, as i like the look of Xubuntu and want to surf the web on it as well, and play with linux.

ill try what you said once i get it to cooperate*.

*i think its the CD drive i was using, but an error kept poping up when i was trying to reinstall Xubuntu, and its working right now, and no error, lookin good

ill tell ya how it went when i am able to test it.

---

