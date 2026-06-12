---
title: "Playing with Xdmx"
date: 2007-01-05
forum: General Help
---

### Post by chrroessner on 2007-01-05
Hi,

I am trying to get XDMX working here with my PC and my laptop.

1. I changed both gdm.conf files and anabled TCP listining,
2. On both machines I logged in via gdm as normal user using the resuce session
3. On the client, I entered xhost + 192.168.3.150 (my PC´s IP address - the controller)
4. On my PC I typed:

startx `which gnome-session` -- /usr/bin/Xdmx :1 -display 192.168.3.34:0.0 -display 192.168.3.150:0.0 +xinerama -input 192.168.3.150:0.0

4. gnome is starting up in xinerama mode, but as you can see in the screenshots, there are no pixmap images. So my question is, why? The screenshot can be found here:

[http://www.roessner-net.com/images/screenshot.jpeg](http://www.roessner-net.com/images/screenshot.jpeg)

Do I have to start the gnome-session with a different command?

I like that multihead stuff :-) So, any help is really much welcome. If I get this thing done working fine, I will write a little Wiki-Howto on that.

Regards
Christian

---

### Post by chrroessner on 2007-01-07
bump

---

### Post by chrroessner on 2007-01-08
Hi,

in the meantime I have checked my xorg.confs on both machines. For testing purposes I set both X setups to the vesa driver with 1280x1024, but the result is the same, if starting gnome-session, all the images as seen in the screenshot are missing.

Nobody any idea? :-( Please

Regards

Christian

---

### Post by chrroessner on 2007-01-09
Got it:

This is my startscript:

```

#!/bin/bash

startx /home/croessner/bin/gnome-xdmx.sh -- \
        /usr/bin/Xdmx :1 \
        -display 192.168.3.152:0.0 \
        -display 192.168.3.150:0.0 \
        +xinerama \
        -input 192.168.3.150:0.0 \
        -norender

exit 0

```

where /home/croessner/bin/gnome-xdmx.sh is:

```

#!/bin/bash

for i in /etc/X11/Xsession.d/*
do
        source $i
done

exit 0

```

The latter script needs some changes, because dbus-launch does not start.

Does anybody know, how gdm is starting a regular gnome-session? Which process is reading all the files in /etc/X11/Xsession.d ?

Thanks in advance

Christian

---

### Post by MilesTeg on 2007-02-22
Hi I'm also trying to get Xdmx working under Ubuntu.

I followed the tutorial at [http://www-128.ibm.com/developerworks/linux/library/os-mltihed/index.html](http://www-128.ibm.com/developerworks/linux/library/os-mltihed/index.html) but I always get the following error messages:

dmx: dmxOpenDisplay: Unable to open display :0

IO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 0 requests (0 known processed) with 0 events remaining.



Seems the PCs can't connect to the X-Server. Any ideas? :confused:

---

### Post by worik on 2008-01-28
> **MilesTeg said:**
> Hi I'm also trying to get Xdmx working under Ubuntu.

I followed the tutorial at [http://www-128.ibm.com/developerworks/linux/library/os-mltihed/index.html](http://www-128.ibm.com/developerworks/linux/library/os-mltihed/index.html) but I always get the following error messages:

dmx: dmxOpenDisplay: Unable to open display :0

IO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 0 requests (0 known processed) with 0 events remaining.



Seems the PCs can't connect to the X-Server. Any ideas? :confused:

You must ensure that both X servers are listening on TCP.

Use netstat

sudo netstat --inet -lnp -t|grep X

You should see something like...

tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     21761/X  

Next ensure that all the computers can connect to the input machine.  So far I have only tried this on two machines.  foo and bar

On foo run: xhost + bar
On bar run  xhost + foo

Then I run...

startx /usr/bin/twm -- /usr/bin/Xdmx :1 -display 192.168.1.11:0 -display 192.168.1.13:0 -ignorebadfontpaths +xinerama -noglxproxy

But twm does not run.  I have a cross cursor and when I right click I do not get the twm menu.

startx /usr/bin/gnome-session -- /usr/bin/Xdmx :1 -display 192.168.1.11:0 -display 192.168.1.13:0 -ignorebadfontpaths +xinerama -noglxproxy

Fairs no better.

The script above does not help.

That is where I am up to.

Worik

---

### Post by worik on 2008-01-30
I got this a bit wrong.

The TCP stuff is fine.

foo is the machine I have my keyboard and mouse on
bar is the other machine 
> 

On foo run: xhost + bar
On bar run:  xhost + foo


Should be...
On foo run: xhost + foo
On bar run:  xhost + foo


> 
startx /usr/bin/twm -- /usr/bin/Xdmx :1 -display 192.168.1.11:0 -display 192.168.1.13:0 -ignorebadfontpaths +xinerama -noglxproxy


For bar to left of foo
startx /usr/bin/twm -- /usr/bin/Xdmx :1 -display bar:0 -display foo:0 -input foo:0 -ignorebadfontpaths +xinerama 

I have stopped using -noglxproxy

But even better I use a script

#!/bin/sh
xhost +local:
unset XAUTHORITY
export NEWDISPLAY=:1

# Start Xdmx
Xdmx $NEWDISPLAY   -display bar:0 -display foo:0 -input foo:0 +xinerama -ignorebadfontpaths &
export DISPLAY=$NEWDISPLAY
sleep 2  # give it time to come up

# Select your window manager
# Gnome should not have a SESSION_MANAGER variable set.
unset SESSION_MANAGER
gnome-session  &


Starts a Gnome session!
Worik

---

### Post by brack on 2008-03-25
tried both scripts, tried to figure out myself, tried some other tutorials.... two days of troubles. The maximum I get so far is running gnome session as root or see pure x screens on my monitors. Sooooo tired. one time I did what was desinged, run gnome on two screens as user, but after restart of computers no luck any more.

Any practical adwise would be upreciated

---

### Post by brack on 2008-03-26
Ok Now it works in user mode, I used the first script introduced on this page. BUT now I have to abilities to switch keyboard layouts!!! I have three layouts english swedish and russian phonetic I have following in xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,se,ru(phonetic)"
	Option		"XkbOptions"	"grp:alt_shift_toggle"
EndSection
```

but when I right-click on gnome's keyboard layout switcher it shows there only one group availabe "U.S.English" the other layouts are setup as well, but there are question marks in switcher instead for SE or RU. If I press Alt-Shift I get layouts switched but only english and swedish no russian. What to do?

---

### Post by brack on 2008-03-31
had to move back to synergy so far, but still looking forward to setup xdmx, so, if someone knows the answers on my questions in this topic, or if someone doesnt have ANY problems with running xdmx on their system, please reply.

---

### Post by brack on 2008-05-09
Apparently there is no XDMX package in Ubuntu 8.04LTS, Wondering if there is any replacement for the features provided by that package?

---

### Post by diaa on 2008-05-09
> **brack said:**
> Apparently there is no XDMX package in Ubuntu 8.04LTS, Wondering if there is any replacement for the features provided by that package?

I got it manually from gutsy repositories and it installs fine, but I haven't tried it yet, here's the link
[http://packages.ubuntu.com/gutsy/xdmx](http://packages.ubuntu.com/gutsy/xdmx)

---

### Post by brack on 2008-05-14
> **diaa said:**
> I got it manually from gutsy repositories and it installs fine, but I haven't tried it yet, here's the link
[http://packages.ubuntu.com/gutsy/xdmx](http://packages.ubuntu.com/gutsy/xdmx)

Yeah I also got it manually from their site by converting rpm to deb. Didnt have problem to install, but I wonder if it was removed from repositories because it didnt work soothe or some other reasons?

---

### Post by sailingboarder on 2008-06-05
bump

is there a particular reason why the xdmx package was removed from hardy

also, how do i install the gutsy package in hardy

---

### Post by brack on 2008-06-11
> **sailingboarder said:**
> bump

is there a particular reason why the xdmx package was removed from hardy

also, how do i install the gutsy package in hardy

Would like to know it too, maybe a good question to developers? or there are some other packages that do similar job? Otherwise there is no packages serving this purpose left in repositories.

---

