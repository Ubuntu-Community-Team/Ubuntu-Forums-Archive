---
title: "Fixing screen res in command line"
date: 2008-02-21
forum: General Help
---

### Post by zorlab on 2008-02-21
just recently installed Ubuntu 7.10 and the screen was looking bad, flickering and all so I upped the screen res and put in 85 hrtz refresh rate. -=dont know what it should be.
Well after fixing it up having a nice dektop of my choice, resizing to fit the screen, and doing some setup of mail. Ubuntu froze.
I restarted in safe mode, typed  startx.  aha! I  see that the virtual screen width is set to 2048, says the max ix 2032.  
So what would be the code on the comand like to fix this? 

any help is areciated :)

---

### Post by SpaceTeddy on 2008-02-21
on the commandline, open an editor (pico, nano, vim are choices you have here) and edit the file found in "/etc/X11/xorg.conf" (command would be "sudo pico /etc/X11/xorg.conf")

that one should contain the allowed resolutions for your screen - if you delete all the res that are too hight, gdm or kdm (which ever you use) as well as the xserver will not pump the res up to really high definitions...

also, if that does not work, try running "sudo dpkg-reconfigure -phigh xserver-xorg" which will let you reconfigure your xserver in a dialog driven menu...

hope you can get it working with that...

---

### Post by mbeierl on 2008-02-21
You are able to access a terminal?  Is it possible for you to post the contents of your /etc/X11/xorg.conf file, please?

---

### Post by zorlab on 2008-02-21
> **mbeierl said:**
> You are able to access a terminal?  Is it possible for you to post the contents of your /etc/X11/xorg.conf file, please?

will do after i copy it, ....remeber i am in windows now   ;0)

---

### Post by zorlab on 2008-02-22
i am lost here...  Tried both sugestions, to no avail.
 the xorg.conf  is corrupted, get error on line 104, ~~>now way I  know how to fix it. 
I did change the line that had 2048, to 2032, but that didnt help. (there was other input info (lenghth?) but I didn't know what to put there.
Then I put back the 2048 in the line.

When I try  " sudo  dpkg-reconfigure xorg-xserver" I get no such file..
Tried to install it, there isn't such a thing in the repositories.

Where do I go from here?
Any way I can get a good xorg.conf? And if I can, how do I resolve the resolution issue?
:confused:

---

### Post by bodhi.zazen on 2008-02-22
Boot to recovery mode (it is an option on the grub or boot screen). This will boot to a command line where you are root.

enter this command :

```
dpkg-reconfigure -phigh xserver-xorg
```

Always remember to back up system files before you edit them ;)

Reboot.

---

### Post by zorlab on 2008-02-22
Thanks, that got me to the GUI, however,  now I cannot change the screen res. when I use the interface it simply stays in a flickering poor quality default resoution (1200x1600 seems like an odd default!)

Assuming I get the change resolution to work, what should the setting be?  ballpark dimensions  :) so I dont get shut out of xserver again.:)

---

### Post by bodhi.zazen on 2008-02-22
What videocard and monitor are you using ?

---

### Post by zorlab on 2008-02-22
NVidia Vanta LT nothing secial, old vid card
and old 17 inch CTX Monitor

---

### Post by bodhi.zazen on 2008-02-22
You may want to try the nvidia driver ...

Envy is the easiest way to install it : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by zorlab on 2008-02-23
thanks again, I was begining to think it could be the drivers, since, my experience with Windows resolution probelm are similar, in that it wont allow good configurations unless the drivers are right.

You gotta love linux!  the next time I logged in a pop up dialog box alerted me that the resolution was not good, would you like to fix it? I input a good resolution I have used in the past, but it defaulted to 800x600 which is fine for now, no more flickers. So in essence, Ubuntu fixed itself. It reconfighred the inappropriate 1200 x 1600 default i could not fix, to a 800 x600 that I cannot fix also, but can live with!

Now on the drivers...

Is there an apt-get install line or way to go to the drivers in the command line?
Should I just go the the url you gave me from Ubuntu?

Its really a bitch to get to your posts unless you have dragged a shortcut to your desktop or subscribed to it!  this place is really busy!

---

### Post by zorlab on 2008-02-23
***deleted*****

---

