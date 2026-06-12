---
title: "change screen resolution and now black screen"
date: 2008-01-14
forum: General Help
---

### Post by gtpgrandprix on 2008-01-14
Hi, my name is josh and i just had ubuntu installed on my gateway t-series laptop. I currently have vista as my main os. My problem is this, as soon as i logged on to ubuntu the screen resolution was not filling the whole screen (sorta like a web page that is 600px wide align right). I went to the screen resolution menu and changed the resolution. this is when the screen went completely black!!!! I have tried to log in as gnome terminal all of it nothing works still black. the login page is fine but once i go passed the login page all i get is black. I need help because I hate vista!!!!! Thanks for future help.::confused:

---

### Post by gtpgrandprix on 2008-01-14
ok so i used crtl alt f1 and got to a command prompt and it said that 2 different resolution weren't working but a 3rd was its now asking for a command what should input?

---

### Post by Digger78 on 2008-01-14
```
startx
```

when you have loaded the desktop, open a terminal

post the output from

```
cat /etc/X11/xorg.conf
```

If x fails to start

```
sudo nano /etc/X11/xorg.conf
```

scroll down to   **Section "Screen"**

delete the resolutions that dont work, leaving the good resolution

press **ctrl+x** to exit

then try starting X again

```
startx
```

---

### Post by gtpgrandprix on 2008-01-14
ok i ran the /etc/XLL/xorg.conf and got a screen that has on the top bar 
GNU nano 2.0.6                                  /etc/XLL/xorg.conf                                   modified




                                         blank in the middle



at the bottom it has ^g get help ^writeout ^read file etc....

what do i do? sorry brand new to linux

---

### Post by gtpgrandprix on 2008-01-14
all that code opened was a text editor. should i reinstall it?

---

### Post by Digger78 on 2008-01-14
there was no content in  the file?

you can reconfigure xorg with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gtpgrandprix on 2008-01-14
i think this might work i am trying to find out my resolution and refresh rate right now

---

### Post by gtpgrandprix on 2008-01-14
I went through the whole configure setup and select my right screen size and still right after i plug in my login info and press enter the monitor turns off. help

---

### Post by Digger78 on 2008-01-15
do it again but for now ONLY select low resolutions

800x600  640×480   @60 Hz

we can try and get the higher ones later

---

### Post by gtpgrandprix on 2008-01-15
k im going to try thanks for the help...

---

### Post by gtpgrandprix on 2008-01-15
i get to the 24 bit color menu and press enter then this comes up at the bottom of the screen:
xserver xorg postinst warning: overwriting possibly-customised confguration 
file backup in /etc/xll/xorg.conf.20080115001752
what do i do now?

---

### Post by Digger78 on 2008-01-15
```
startx
```

---

### Post by gtpgrandprix on 2008-01-15
startx just says:
fatal server error:
server is already active for display 0
if thi sever is no longer running, remove /tmp/.xo-lock and start again
dunno what to do

---

### Post by Digger78 on 2008-01-15
```
sudo reboot
```

---

### Post by gtpgrandprix on 2008-01-15
nothing is working how do you unistall this?

---

### Post by Digger78 on 2008-01-15
uninstall what?

you have not installed anything with the commands in this thread.

---

### Post by gtpgrandprix on 2008-01-15
just want to unistall linux this is not working at all

---

### Post by DarthTibault on 2008-01-15
> ok i ran the /etc/**XLL**/xorg.conf

no wonder it doesn't work: it's X11 not XLL

---

