---
title: "Drivers for Intellimouse Explorer Mouse"
date: 2007-03-26
forum: General Help
---

### Post by TreeFinger on 2007-03-26
I recently reinstalled Ubuntu. I am using a Microsoft Intellimouse Explorer 4.0 and I am wondering if there is anywhere I could find drivers.

I just like being able to use the side buttons to go forward and backward on webpages or while I am exploring directories. Thanks for any help in advance.

---

### Post by Toadmund on 2007-03-26
I have a microsoft mouse as well, the one with the red thumb ball, I just discovered recently (when I was still on XP) that the shoulder buttons made be go back and forward, a real convenience.
These buttons do not work with Ubuntu, even though my mouse still does everything it needs to.
It would be nice to have a GUI that one could use to customize your mouse buttons, I find the current 'system-->preferences-->mouse' too basic, it could be more customisable, like a joystick callibrator, but for your mouse, something like that.
Not too crucial though.

---

### Post by cmapesjr on 2007-03-26
Same boat here. I would really love some suggestions for this issue.

---

### Post by TreeFinger on 2007-03-27
Would this topic be better if I moved it somewhere else?
I miss my forward and back buttons :( I am always hitting them and waiting and then I realize it doesn't work. :lolflag:

---

### Post by cmapesjr on 2007-03-29
Maybe so. At your leisure. :)

---

### Post by Wiebelhaus on 2007-03-31
aye , this is bothering me a bit.

---

### Post by Wiebelhaus on 2007-04-01
> **sx66gns said:**
> aye , this is bothering me a bit.

I seem to be answering allot of my own questions, this was buried deep within support docs..


   1. Backup your xorg.conf file (ALWAYS backup this file before even thinking about touching it): sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
   2. Edit the file: sudo nano gedit /etc/X11/xorg.conf
   3. Find the Section “Input Device” for your mouse and change the following:

    Section “InputDevice”
    Identifier “Configured Mouse”
    Driver “mouse”
    Option “CorePointer”
    …..
    Option “Protocol” “ExplorerPS/2&#8243;
    …..
    Option “Emulate3Buttons” “true”
    EndSection

to include the multiple button mouse support:

Section “InputDevice”
Identifier “Configured Mouse”
Driver “mouse”
Option “CorePointer”
…..
Option “Protocol” “ExplorerPS/2&#8243;
…..
Option “Emulate3Buttons” “true”
Option “Buttons” “7&#8243;
Option “ButtonMapping” “1 2 3 6 7&#8243;
EndSection

At this point you can restart your computer (or possibly just GNOME using ctrl-alt-backspace). You should then have support for your additional buttons within Firefox. Enjoy your world domination!

Honestly , this should be plugged into the mouse configuration interface.

---

### Post by cmapesjr on 2007-04-03
Thank you so much for looking into this. I will try and get it done this weekend.
I will let you know how it works out. :guitar:

---

### Post by JLAudioFan on 2007-04-08
I tried the steps that sx66gns mentioned above, and didn't have much success... However, after checking the forums for a while, I found what I think is the missing piece of info...

I did steps 1 and 2 in this post
[URL="http://ubuntuforums.org/showthread.php?p=2411889"]
http://ubuntuforums.org/showthread.php?p=2411889[/URL]

and it worked like a charm :)

Hope it works for ya!

Jason

---

### Post by jayshomebrew on 2007-04-15
Steps 1 & 2 worked for me too. intellimouse explorer 4.0
[IMG]http://img388.imageshack.us/img388/4564/prodtopmimexmd9.jpg[/IMG]

---

### Post by piracyrocks on 2007-11-01
does the tilting of the scroll wheel work with this guide?

---

