---
title: "Login Keyboard unresponsive after X starts"
date: 2008-06-22
forum: General Help
---

### Post by real_ate on 2008-06-22
Hey everyone, first time actually looking for help in quite some time! No news is good news in the support section eh? ;) 

anyway, the problem is a strange one so i'm looking for help and some way to get some diagnostic info on it too so if anyone can help with that please jump in too. 

right... so when Kubuntu loads up to the login screen my keyboard just doesn't work! mouse is working fine and the keyboard is working fine just up until the login screen ( i.e. it works in the bios, in grub and in the failsafe mode ). 

This problem used to happen only 20% of the time and a restart would fix it but now i'm at 100% of the time! which is not so great! 

other information: i can no longer ssh into the box, or ping it. ( strange but true )! 
I was originally working off a wireless RF mouse and keyboard with the mouse working fine and just the keyboard out of order but its not the usb problem cos i tried a PS2 keyboard with the same problems. 
I'm running 8.04 Kubuntu. 

I think thats it, any suggestions on fixes or logs i should be looking at would be much appreciated. Thanks!

---

### Post by fahadsadah on 2008-06-22
What keyboard are you using?

---

### Post by real_ate on 2008-06-22
well the first one that i was using was a mikomi RF wireless ( LK-802A ) usb keyboard, but i have pretty much made sure it wasn't the keyboard that was the problem cos i tried it again with a generic IBM PS2 keyboard.

---

### Post by real_ate on 2008-06-22
Ok, 3 hours and a cricket match later its back working again... don't suppose anyone could point me to the correct log files so i can see what was going on?

---

### Post by Zorael on 2008-06-22
dmesg log:
```
$ dmesg > ~/dmesg.log
```
Then open up the new **dmesg.log** in your home directory with a text editor and see if something stands out.
```
       dmesg is used to examine or control the kernel ring buffer.

       The program helps users to print out their bootup messages.  Instead of
       copying the messages by hand, the user need only:
              dmesg > boot.messages
       and mail the boot.messages file to whoever can debug their problem.
```


X.org's log (the graphical environment): **/var/log/Xorg.0.log**

---

### Post by Rowd on 2008-06-24
I have the same problem, but i also noted that trying to shut down or restart the computer from the menu in gdm, the screen turns black and gets frozen, then the only way of restarting is doing the alt+print-screen+REISUB thing...

also, it seems that if i press any combination of keys when ubuntu is starting, its more probable that the keyboard will work, and if i start in recovery mode and then continue the normal boot, it always works fine.

---

