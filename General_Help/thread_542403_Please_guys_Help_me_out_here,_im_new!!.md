---
title: "Please guys Help me out here, im new!!"
date: 2007-09-03
forum: General Help
---

### Post by Sargent_Peper on 2007-09-03
Ok i made a bo bo with my Kubuntu Feisty installation on my system. I changed the video driver From ATI fglx.....something, to the VESA driver because i wanted to see if it would work better......well......it doesnt....now when i boot up i see nothing but horizontal (angled) lines...i see (somewhat) the mouse pointer moving in the back but i cant make any changes because i cant see nothing. Is there a way to get back to normal. if i was in Windows i would boot in safe mode.....but i aint......and i dont know how to boot in safe mode in Kubuntu.........not the live cd now guys......a real installation. My Kubuntu has been installed on my system for a while, few months, i have no problems. k my system: AMD Athalon 2500+ 1 gig ram, 250 gig hd, ATI Radeon 9600 XT 256 megs ram, Sound Blaster Live, onboard lan, 1 cd burner, 1 DVD burner. No other OS is installed. Please help!!!!!

---

### Post by buzzmandt on 2007-09-03
i run nvidia so not sure, but you can restart in recovery mode, login
then type```
sudo vim /etc/X11/xorg.conf
```

find driver, probably the same one you change to vesa and change it to fglrx.
```
Driver "fglrx"
```

---

### Post by yabbadabbadont on 2007-09-03
If kubuntu is the only OS installed on the machine, then you will need to hit the Escape key when you see the grub prompt.  That will display the grub boot menu.  From there you can choose to boot safe mode.  Once there, run ```
sudo dpkg-reconfigure -p high xserver-xorg
```  After that, your video should be back to its installation default settings once you reboot.  Just type 'reboot' (without the tick marks) and hit enter to reboot.  (or you could hit ctrl-alt-delete and the system will shutdown and reboot)

---

### Post by buzzmandt on 2007-09-03
oh, sorry, I know it's frustrating with controls being noob, as i am also noob  :)

when in vim use arrow keys to move around
get to the line you want to change and you can delete the unwanted code with the delete buttom
press the letter "i" for insert and you can insert code
press esc to exit insert mode
press : (colon) for function mode
type wq and enter to save and exit 
(w is for write to file, q is for quit)

hope i did all the right  :)

noob helping noob, is that like the blind leading the blind?

---

### Post by buzzmandt on 2007-09-03
> **yabbadabbadont said:**
> If kubuntu is the only OS installed on the machine, then you will need to hit the Escape key when you see the grub prompt.  That will display the grub boot menu.  From there you can choose to boot safe mode.  Once there, run ```
sudo dpkg-reconfigure -p high xserver-xorg
```  After that, your video should be back to its installation default settings once you reboot.  Just type 'reboot' (without the tick marks) and hit enter to reboot.  (or you could hit ctrl-alt-delete and the system will shutdown and reboot)

thank you yabba, 

oh well, I tried  :)

---

### Post by yabbadabbadont on 2007-09-03
> **buzzmandt said:**
> thank you yabba, 

oh well, I tried  :)

Your solution will work, it's just that mine is less complicated.  After all, Linux is all about freedom of choice.  :D

---

### Post by Sargent_Peper on 2007-09-03
ok thanks ill try that but i might come back with some new stuff i wont understand. lol.....god i feel like i did 10 years ago with Winblows. lol!!

---

### Post by Sargent_Peper on 2007-09-03
just so you guys know, im only able to post here because i inserted the Kubuntu Cd and ran the live cd, so im running this ontop of my real install. They should put some way of inserting the CD and being able to recover a real install with it, dont you think. or am i too late!! lol!!

---

### Post by Sargent_Peper on 2007-09-03
Woohoo!! thanks guys it worked lovely.......you guys are great!!......you guys answered me really quick......thanks again!! Now....lol!! can anyone tell me how to upgrade my ATI drivers so Kubuntu takes advantage of my kick butt card.....cause i really dont get very good graphics in alot of the free games for this OS.  lol!!

---

### Post by yabbadabbadont on 2007-09-03
Sorry, I run nvidia.  I've read that using the proprietary ATI drivers is sometimes....  problematic.  I'm sure there are plenty of threads about doing so though.  Try searching for "ATI howto".  That may turn up some useful threads.

---

### Post by buzzmandt on 2007-09-03
this might help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Sargent_Peper on 2007-09-04
You bet...thanks ill check that out.  Thanks to all of you guys again....keep it up!!

Cheers

---

