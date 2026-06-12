---
title: "Gnome curtian/shade animation error"
date: 2015-12-06
forum: General Help
---

### Post by maciej234 on 2015-12-06
The arrow on the gnome lock screen is not displaying correctly.   Graphics drivers are installed from the additional drivers program. This  normally happens after I wake the machine from sleep. It  animates/pulses but it looks corrupted.  Typing on the keyboard/clicking the volume button will  show the pull up arrow



[ATTACH=CONFIG]266001[/ATTACH]

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

Try these solutions.

The first is to restart the mouse driver :

> sudo modprobe -r psmouse

sudo modprobe psmouse

That is one possible solution

The other is perhaps animations Mouse:


> sudo update-alternatives --config x-cursor-theme

The file must be like this:

------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme   90       
  1            /etc/X11/cursors/core.theme               30        
  2            /etc/X11/cursors/handhelds.theme          20        
  3            /etc/X11/cursors/redglass.theme           20        
  4            /etc/X11/cursors/whiteglass.theme         20        
  5            /usr/share/icons/DMZ-Black/cursor.theme   30        
  6            /usr/share/icons/DMZ-White/cursor.theme   90 

Press < Enter> to keep the default [ * ] or press a number of selection : 

To restore the default pointer is the number 6 ..

After restarted.       

Thank you

---

### Post by maciej234 on 2015-12-07
Here is another picture that shows the mouse and the arrow.  The graphics are displayed this time

[ATTACH=CONFIG]266019[/ATTACH]

---

### Post by Ricardo_Velasco on 2015-12-07
But the problem was solved??

On the Gnome graphical environment I did not find more information but you could take a video or a little more information about your problem because for me and the problem was solved , sorry if I do not understand the conflict

If I could give more information about the graphical environment in which you work ?.

His version among others, to help


PD: 
could you send me the file will appear to put this command in the terminal?

> sudo update-alternatives --config x-cursor-theme

---

### Post by maciej234 on 2015-12-07
The problem is not the mouse cursor.  The problem is the notification/anination to "pull up" the lock screen.  The animation looks broken from time to time.  Sometimes I will see the first screen shot (distorted computer screen) other times I see the arrow.

---

### Post by Ricardo_Velasco on 2015-12-07
Greetings:

Sorry for not understanding, if I understand your problem now .

Please send what Appears on the Screen When You Put This command :

> sudo update-alternatives --config x-cursor-theme

---

