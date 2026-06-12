---
title: "critical mass"
date: 2007-12-13
forum: General Help
---

### Post by cytg on 2007-12-13
this is the third time this happend to me, in three days.

I remote home, xrdp & x11vnc -allinput - noxdamage

and after some time, my connection is dropped.. cannot reconnect.

i go home to find my machine whizzing as under full load, allthough nothing is respondig ..

turning on the tft yields "no signal" 

keyboard not responding (numlock/capslock lights)

And the real bugger ? System logs show NO trace of the incident ... i have no idea what went wrong... (sounds a bit like a bad disc dont it ?)

Ideas please ?

---

### Post by wirelessmonkey on 2007-12-13
This sounds more like a memory of X11 error... run top or htop in the background and see if your memory/processor useage spikes.

---

### Post by cytg on 2007-12-14
Thx .. so i did that, it went off again, and nothing really suspect going on ...

htop, copy of frozen state ;

  1  [||||                     11.3%]     Tasks: 225 total, 1 running
  2  [|||||                    13.2%]     Load average: 0.21 0.25 0.11
  Mem[||||||||||||||||||||532/2027MB]     Uptime: 10:43:18
  Swp[                      0/5938MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 5331 root      15   0 96092 72828 20992 S 12.6  3.5  5:39.94 /usr/bin/X :0 -br
 7098 god      21   0  408M  165M 11076 S  8.0  8.2  1:23.87 /usr/lib/jvm/java-
 7120 god      15   0  408M  165M 11076 S  7.3  8.2  0:49.31 /usr/lib/jvm/java-
 7094 root      15   0 15624  5040   808 S  2.7  0.2  0:04.75 ./xrdp
 7114 god      15   0  408M  165M 11076 S  1.3  8.2  0:04.11 /usr/lib/jvm/java-
 7092 root      15   0 15624  5040   808 S  1.3  0.2  0:04.94 ./xrdp
 7093 god      15   0 26892 22468 14280 S  1.3  1.1  0:12.13 x11vnc -allinput
 7168 god      15   0  2428  1264   964 R  0.7  0.1  0:11.80 htop
 7121 god      15   0  408M  165M 11076 S  0.0  8.2  0:01.39 /usr/lib/jvm/java-
 7140 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.91 /usr/lib/jvm/java-
 6315 god      15   0 38908 10440  8036 S  0.0  0.5  0:01.23 /usr/lib/gnome-con
 7109 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.29 /usr/lib/jvm/java-
 7103 god      15   0  408M  165M 11076 S  0.0  8.2  0:08.22 /usr/lib/jvm/java-
 7104 god      18   0  408M  165M 11076 S  0.0  8.2  0:00.11 /usr/lib/jvm/java-
 6377 god      15   0 16788  5028  3972 S  0.0  0.2  0:19.29 gnome-screensaver
 7155 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.36 /usr/lib/jvm/java-
 7118 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.25 /usr/lib/jvm/java-
 7164 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.22 /usr/lib/jvm/java-
 7034 god      15   0  8056  1548  1080 S  0.0  0.1  0:00.11 sshd: god@pts/0
 6383 god      18   0 45820  4384  3456 S  0.0  0.2  0:04.55 /opt/google/deskto
 6321 god      15   0 18496 10904  7792 S  0.0  0.5  0:08.82 /usr/bin/metacity
 6369 god      15   0  9380  3356  2896 S  0.0  0.2  0:14.44 /opt/google/deskto
 6323 god      15   0 50936 22048 15144 S  0.0  1.1  0:06.48 gnome-panel --sm-c
 7163 god      15   0  408M  165M 11076 S  0.0  8.2  0:00.22 /usr/lib/jvm/java-
 7107 god      21   0  408M  165M 11076 S  0.0  8.2  0:04.69 /usr/lib/jvm/java-
 6364 god      18   0 28488  9172  6536 S  0.0  0.4  0:06.85 /opt/google/deskto
 6445 god      15   0 28488  9172  6536 S  0.0  0.4  0:06.65 /opt/google/deskto
 6381 god      18   0 10380  3392  2916 S  0.0  0.2  0:03.28 /opt/google/deskto
 7162 god      16   0  408M  165M 11076 S  0.0  8.2  0:00.70 /usr/lib/jvm/java-
 6370 god      15   0 22784  8196  5980 S  0.0  0.4  0:00.13 gnome-power-manage
 6325 god      15   0 98484 33572 21296 S  0.0  1.6  0:05.84 nautilus --no-defa
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit



further ideas more than welcome .. i've been struggeling to gt this setup working xrdp/vnc/mstsc .. and being so close you actually think you were there .. to find out you're not is very very annoying .. :)

---

### Post by krunge on 2007-12-14
> **cytg said:**
> 
 6377 god      15   0 16788  5028  3972 S  0.0  0.2  0:19.29 gnome-screensaver
 

Maybe the screensaver is causing a lot of changes on the screen? E.g. kill it or set to screen blank.

BTW, what is your need for xrdp? (I've never used it.)  Do you get the same problem using a vnc viewer?

---

### Post by cytg on 2007-12-14
ill try that (its allready set to blank out)

Is there something about the data from htop that makes you suspect the screensaver?
(this happens in the middle of me doing something on the desktop too..)

No havent had the problem with regular VNC before .. but never ran x11vnc by itself before, only running it cause its the only server i can run remote via ssh and attach to screen 0 ..

i need xrdp cause some places where i get sent out(consultant) doesnt allow installation of non-approved software... but microsofts remote desktop tool is always there ..

I suspect some application, high priority, enters a loop that eats out 100% cpu ... but htop sure as hell dont catch it in time if its the case.

edit ; I need to get a little setup going at home, i just dont have any windows boxes atm .. but perhaps a virtualbox xp -> localhost will reproduce the issue ... hmm

---

### Post by krunge on 2007-12-14
> **cytg said:**
> 
Is there something about the data from htop that makes you suspect the screensaver?
(this happens in the middle of me doing something on the desktop too..)

Ah, then that probably isn't it. I thought you were not connected when it went into that state.
> 
i need xrdp cause some places where i get sent out(consultant) doesnt allow installation of non-approved software... but microsofts remote desktop tool is always there ..

I see. BTW, newer versions of x11vnc has the```
-ssl
``` option that allows you to connect via a web browser with Java (e.g. [https://my-ip:5900](https://my-ip:5900)). So that might work too.

---

### Post by cytg on 2007-12-14
cool .. ill try that (on a different port, cause firewall nazi's usually block anything not http/https lol)

---

