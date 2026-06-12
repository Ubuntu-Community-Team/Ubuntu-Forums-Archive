---
title: "Mouse dragging problems"
date: 2007-06-24
forum: General Help
---

### Post by neo214 on 2007-06-24
There seems to be a delay between the time you click the mouse and when you move it.

This becomes a problem any time I attempt to drag something with the mouse, the mouse click delay prevents me from clicking a dragging at the same time, this makes highlighting text, or dragging a window difficult. 

Is there any way to make the click on a mouse more sensitive? There doesn't seem to be an option for it in the normal mouse settings for Ubuntu.

---

### Post by Silenus on 2007-06-24
system > preferences > mouse

several tabs there to change settings and speed

---

### Post by neo214 on 2007-06-24
Well I've changed those settings extensively with no solution to my problem.

Just so there is no confusion, my problem is that when I click and drag at the exact same time the mouse will miss what it was originally on and go to another part of the screen, for example if I were to start the mouse at the beginning of this paragraph and then click and drag at the same time I would end up only highlighting about half of the text, leading me to believe that there is some sort of delay in between the time I click and the time it registers as a hold down click (maybe as opposed to a click and let go click)

---

### Post by neo214 on 2007-06-24
is there any fix for this? Anything I could do?

---

### Post by s_h_a_d_o_w_s on 2007-06-24
System -> Preferences -> Mouse -> Motion -> Threshold Set all the way to the left

Sorry you said you tried but that doesnt work? 

If i understand correctly Setting the threshold slider all the way to the elft shouldhelp

:D

---

### Post by s_h_a_d_o_w_s on 2007-06-24
8.4.2.3.&#8195;Motion Preferences (From the help section)

   
                 Acceleration
                
              	
                Use the slider to specify the speed at which your
mouse pointer moves on your screen when you move your mouse.
              

                
                  Sensitivity
                
              	
                Use the slider to specify how sensitive your mouse
pointer is to movements of your mouse.
              

                
                  [B]Threshold
                
              	
                Use the slider to specify the distance that you
must move an item before the move action is interpreted as a drag-and-drop
action.[/B]

---

### Post by warrenfalk on 2007-12-10
I wish people would read original posts before responding.

I had the same problem.  Turns out X was configured to emulate a three button mouse and the delay is it waiting to see if you meant to click both buttons at the same time.

```
sudo gedit /etc/X11/xorg.conf
```

search for "emulate" and disable the 3-button emulation.  Reboot.

---

