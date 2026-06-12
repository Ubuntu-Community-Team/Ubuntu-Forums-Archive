---
title: "Install classic gnome"
date: 2014-10-05
forum: General Help
---

### Post by scrufulufugu517 on 2014-10-05
Hey I'm trying to install ubuntu classic gnome on ubuntu server 14.04 and I want to do it without installing gnome 3 or ubuntu 14.04

PLEASE HELP!!

---

### Post by deadflowr on 2014-10-05
Do you mean gnome classic, like just the desktop. 
No unity, no gnome-shell?
Then gnome-panel should be all you need.
```
sudo apt-get install gnome-panel
```
It should pull in all the other parts you would need to run it, like xorg.(maybe?)
(And a few packages which may seem odd, but that's the way it goes; example, unity-control-center, Ubuntu's fork of the gnome-control-center)

Thinking it over a second, you might also look at Ubuntu mate here
[http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts](http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts)

---

### Post by scrufulufugu517 on 2014-10-06
That didn't work. It downloads. Installs, then... Nothing. The only reason I want a GUI is so I can get my wifi adapter working.

---

### Post by nerdtron on 2014-10-06
Have you already configured your /etc/network/interfaces file?

Post #2: [http://ubuntuforums.org/showthread.php?t=2228849](http://ubuntuforums.org/showthread.php?t=2228849)
or here: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal)

---

### Post by deadflowr on 2014-10-06
Did you try a simple 
```
startx
```
it might not have installed a display manager, like gdm, or lightdm.

But this might help get the wifi going
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by nerdtron on 2014-10-06
^Oh yes, if you already installed a GUI, your should manually start it.

---

### Post by scrufulufugu517 on 2014-10-07
ok to make this easier. 

I want to install ubuntu 12 desktop on my server. Is that better?

P.S. other then that my main goals are to host an apache web server, get my website running with my own domain name, and host a samba picture share server.

---

### Post by scrufulufugu517 on 2014-10-07
Also, when I update the kernel I can no longer view the Its working page but webmin still works

---

