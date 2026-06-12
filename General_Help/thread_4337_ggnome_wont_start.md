---
title: "ggnome wont start"
date: 2004-11-14
forum: General Help
---

### Post by blubber on 2004-11-14
First of all sorry for my bad english!

Installaltion works fine.gdm starts my mouse doesnt work,the drums are playing all the time,and gnome does not start,i can see the brown background and the ubuntu logo.but when i put in another mouse i can solve prob 1 and 2,but gnome still does not start.any idea!

my pc
amd 1700xp
geforce 4mx
512 mb ddram
wlan dwl 510
net rtl8139
mouse logitech usb(the one that does not work)

---

### Post by sfw5000 on 2004-11-14
What exactly does happen? I mean, if gnome isn't starting, what is the brown background you are seeing? Is that the login screen (GDM). When you log in, does gnome begin to start, then freeze? Not sure what you mean by the drums. Give as much detail as you can.

---

### Post by blubber on 2004-11-14
i enter my username at the gdm login,then gnome is starting,but it stops,the only thing i can see is that brown background and the ubuntu logo.

ps:its the sound when gdm starts,its playing again and again.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=blubber]i enter my username at the gdm login,then gnome is starting,but it stops,the only thing i can see is that brown background and the ubuntu logo.

ps:its the sound when gdm starts,its playing again and again.[/QUOTE]
 try hitting ctrl+alt+F1 and logging in, typing in "sudo killall gdm" then try "startx" and see if that gets you all the way into Gnome.

---

### Post by blubber on 2004-11-14
thx for your reply,but i have tried this too,andit does not work too.

---

### Post by sfw5000 on 2004-11-15
Since you have an nividia card you might want to follow ubuntu geek's directions here:

[http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

from GDM select failsafe terminal from the Sessions menu and try to get a terminal that way.

---

### Post by blubber on 2004-11-15
Hi again.I solved the problem and ubuntu is running now,had to change the mouse,and made a few changes in my bios.Now ive got another prob,cant load my wlan with ndiswrapper under slackware i had no problems.Perhaps the 2.6 kernel?
dmesg gave me this message:
ndiswrapper (hangcheck_bh:390) Hangcheck returned true. Resetting wlan0

and iwlist wlan0 scan says

wlan0 no scan results

any idea?

or ist there a driver for my wlan card dlink dwl-510?

one more question when i install packages from sources how can i uninstall  them? 

thx for your help

Benedikt

---

### Post by basse1989 on 2004-11-19
I have the same problem. GDM works, the drums are playing and gnome wont start. I login and all I can see is that brown background and the ubuntu logoed splashscreen. The network card doesn't work either. Ubuntu don't seem to detect it, even tough I have a Realtek card that use to work with the module 8139too.

---

### Post by bruce2k on 2004-11-23
hi!

i've got the same problem. i tried to install ubuntu on my notebook with a geforce 4 mx - everything works fine except from the gnome start. i used gdm to log in and then - brown background / ubuntu splash / nothing else. i was waiting for about 10 minutes without success. what may i chance in the bios to get a workling gnome? please help me, i really like ubuntu and don't want to use another distribution.

thx, bruce

---

### Post by jdong on 2004-11-23
[b][u]One question per topic please!
 
 [/u][/b]I've seen a few of these posts already, with either 'infinite-drumming' or some sort of GNOME hang.
 
 I think this deserves a spot in Stumper Questions/.

---

### Post by taygan on 2004-12-15
I had the infinite drumming this problem on my Thinkpad 600, removing the sound modules let Gnome boot.. maybe check /etc/modules I still haven't figured out how to have sound load at boot on that machine.

The other computer (ASUS A7V600-X mobo) wouldn't load because some .config files were owned by root, not me..  Make sure that /home and /home/$USER and /home/$USER/.'gnome config files' are owned by you.

Good Luck

---

### Post by Uuranor on 2005-01-03
Perhaps it is the same my problem.
Have you pppoe active at startup of gnome? 
Try to turn off the modem (if you have an adsl ethernet).

I have explained my problem at this link: [http://www.ubuntuforums.org/showthread.php?p=42576#post42576](http://www.ubuntuforums.org/showthread.php?p=42576#post42576)

---

