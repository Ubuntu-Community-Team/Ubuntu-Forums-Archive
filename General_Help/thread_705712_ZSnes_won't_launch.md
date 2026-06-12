---
title: "ZSnes won't launch"
date: 2008-02-23
forum: General Help
---

### Post by skydiver|goose on 2008-02-23
I just installed ZSnes on my Ubuntu laptop so I could keep myself entertained at work, but it won't launch.

I installed it using "sudo apt-get update" "sudo apt-get install zsnes" and the packages read fine and everything, but when I click the icon to launch the program, it launches for about 10ms, then automatically closes itself.

any ideas?

---

### Post by pointone on 2008-02-23
Try running it from the command line to see if it throws any error messages.

---

### Post by skydiver|goose on 2008-02-23
how can I get it to run in the command line?

---

### Post by skydiver|goose on 2008-02-23
goose@goose-laptop:~$ sudo /home/goose/Desktop/zsnes.desktop
[sudo] password for goose:
sudo: /home/goose/Desktop/zsnes.desktop: command not found
goose@goose-laptop:~$

---

### Post by skydiver|goose on 2008-02-23
got it. in case anyone else has the same issue with it, just open a terminal window and type "zsnes"

---

### Post by skydiver|goose on 2008-02-25
new issue. here's what I see in terminal:

goose@goose-laptop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/goose/.kde/socket-goose-laptop.
can't create mcop directory
goose@goose-laptop:~$ sudo zsnes
[sudo] password for goose:
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 3 mice detected.
Using ManyMouse for:
Mouse 0: AlpsPS/2 ALPS GlidePoint
Mouse 1: PS/2 Mouse
Creating link /root/.kde/socket-goose-laptop.
can't create mcop directory
goose@goose-laptop:~$

---

### Post by mastahkillah666 on 2008-02-25
Your fix is [[COLOR="Red"]HERE[/COLOR]]("http://ubuntuforums.org/showthread.php?t=593888"). Be sure to read the whole thread in order to understand the mechanism behind the error.

Hope it helps.
See ya around the forums.

---

### Post by Ewingo401 on 2008-02-27
That tutorial helped get zsnes working.  But does anyone have any idea on how to get a logitech usb controller to work with it?

---

