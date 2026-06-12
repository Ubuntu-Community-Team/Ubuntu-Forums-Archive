---
title: "Help..."
date: 2007-12-24
forum: General Help
---

### Post by Psyco_Chipmunk on 2007-12-24
Hi,  i just tryed dual monitored on my laptop.  It worked pretty good but i dident want the other monitor anymore, so i disconected it and put the dual monitor settings back to single.  So it tells me to restart my computer, so i do that and now this comes up.

starting up ...
[       0.000000]  acpi: dMI bios YEAR==0, ASSUMING acpi-CAPABLE MACHINE
loading, please wait...
kinit: name_to_dev_t(dev/disk/by-uuid/2c592b15-of3e-47e3-a4bd-e273e2dba
c3e
kinit: No resume image, doing normal boot...

Ubuntu 7.10 luke-laptop tty1

luke-laptop login:_   So i put in my login
Password: and password

-Just tells me my last login and crap...

-Tells how ubuntu has no warranty

luke@luke-laptop:~$  



So what do i do?  How do i log in?

Is my computer ruined??? 

Help?!:confused:

---

### Post by taurus on 2007-12-24
You just have to reconfigure your X server for one monitor now.

At the prompt, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, see if X is running again with

```
startx
```

---

### Post by Psyco_Chipmunk on 2007-12-24
hah!  I thought my computer totaly got messed up!  Thanks so much!  Merry Christmas, god bless.:lolflag:

---

### Post by staticvoid on 2007-12-24
whenever you get


luke@luke-laptop:~$ 

you are in your computer. getting around is just different without the GUI.

you can type ls it list the files in the curent directory or cd <name of directory> to change folders and then you can cp and mv and rm files all over the place.

:)

glad you Got it fixed though.  Merry Christmas

---

### Post by davidingram on 2007-12-29
Hi, I had almost the exact same problem as this, after using an external monitor.
Did the xserver config that is mentioned here and all appeared fine at first, i goit my GUI back when i did startx.
BUT, now I have no "shutdown" option on my shutdown button (just 'hibernate', ;suspend' etc).  I just tried to hibernate with the intention of resuming from there, thinking it would sort itself out after a restart, but now I dont get the UI, and I dont get the cmd prompt.  I just get a black screen, a mouse pointer, and a few seemingly random red pixels lit up in the bottom left and bottom right of the screen.  

HELP, Am i totally screwed???

---

### Post by davidingram on 2007-12-29
jeez, this is killing me, i have managed to get it to start to the prompt again (some sort of safe restart by hitting esc during the boot), and i've tried this xserver config again, but now i cant do "startx", it tells me

xauth: creating new authority file /home/david/.serverauth.4567
X: user not authorized to run the X server, aborting.
startx
giving up
xinit: Connection refused (errno 111): unable to connect to x server
xinit: No such process (errno 3): Server error.
david@david-home:~$

Any ideas will be gratefully received.

---

### Post by jlh on 2007-12-31
I am getting the same boot into the terminal described at the beginning of this post.  I never installed a second monitor.  This is a very recent development, suggesting to me that it may be linked to an update.

When I get the login prompt in the shell, if I wait, usually the login gui splash screen appears.  Sometimes it takes my user name and password normally.  Sometimes, it responds very sluggishly, and autocomplets a whole bunch of non-inputed characters (in the form of black dots) that fill the password screen.  Then, of course, the log in fails.  A second try usually works.

However, when I get past the login screens, half the time the computer hangs at the desktop.  Nothing loads, and I see a beige screen.  Control-Alt-Backspace sends me back to the login screens, and after one or two tries, the desktop boots the way it should.

All this is very recent - the past week or so.

---

### Post by davidingram on 2007-12-31
Hi, I got my problem fixed here: [http://ubuntuforums.org/showthread.php?t=459780&goto=newpost](http://ubuntuforums.org/showthread.php?t=459780&goto=newpost)

Maybe this will help you.

D

---

