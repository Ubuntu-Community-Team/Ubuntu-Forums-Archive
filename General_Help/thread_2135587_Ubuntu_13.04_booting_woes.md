---
title: "Ubuntu 13.04 booting woes"
date: 2013-04-14
forum: General Help
---

### Post by meijin3 on 2013-04-14
I installed 13.04 on my laptop and it was GREAT! Super fast, super beautiful, everything I could want in an OS. Now it will not boot, however :( After the GRUB menu, it has a purple screen for about a minute, then this screen for an extremely brief amount of time (it was very hard getting a screenshot from the video I took): 

[IMG]http://i.imgur.com/p22Mx7Kl.jpg?1[/IMG]

And finally a black screen. I installed  a proprietary graphics driver and it worked for some time after this. Can anyone tell me where to start fixing this thing?

**Final Edit: **Solved! I was able to fix the problem myself. After getting the black screen I pulled up terminal by using "ctrl"+"alt"+"f1" and I input: ```
sudo apt-get remove fglrx-updates
``` The next time I booted up, I was working!

---

### Post by meijin3 on 2013-04-14
Bumpity, bump, bump! If someone can point me in the right direction, I'd appreciate it :)

---

### Post by Impavidus on 2013-04-15
Please be patient. Bumping after 24 hours is accepted here.

Although I'm not the specialist on these matters, I'm sure it would help if you gave some details on your hardware, specifically your graphics card. Tell us make and model. Also give your CPU and RAM, although I don't think the problem is there.

---

### Post by meijin3 on 2013-04-15
Sure, and sorry for the premature bumping. 

I have an HP Pavilion dv6 with AMD A8-3500 APU and Radeon HD Graphics clocked at 1.5 GHz. I've also got 8 gigs of RAM.

---

### Post by grahammechanical on 2013-04-15
Could you please confirm if this happened before or after the installation of the proprietary video driver? Your first post seems to hint that installing a proprietary driver fixed this. Did it? Or did it re-occur?

You do know don't you that 13.04 is still under development. I am using it myself. I have been since November. Changes are still being made even with less than 2 weeks to go (I think). We are getting Kernel upgrades and I think I saw an X-server upgrade a day or two ago. Things get broken. Sometimes it is due to an incompatibility with proprietary video drivers. I had to switch from the Nvidia driver to Nouveau the other day because an update to the kernel broke the desktop - no Unity.

If you select Additional Options for Ubuntu at the Grub menu you will see an option to load in Recovery Mode (second on the list, I think) You can try Recovery>Resume. That will sometimes get us to a desktop. These things sometimes get fixed by a further update to the system.

Regards.

---

### Post by pfeiffep on 2013-04-15
I just received a kernel update a few minuted ago

---

### Post by meijin3 on 2013-04-15
@grahammechanical: My problems occurred after installation of the proprietary driver, however it worked for quite a few boots after doing so, iirc. As a note, I had an "Unsupported Hardware" watermark that I tried correcting via a method similar to, or possibly the exact same one as, the one shown in the following link: [http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver](http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver) (I can't find the exact page I went to). I do realize Ubuntu 13.04 is under development but got a new laptop and thought it would *possibly* be stable enough at this point to use and I didn't want to mess with upgrading from 12.10 to 13.04 if I didn't have to. I have not been successful trying to boot into recovery in the past couple of days, but I will give it another shot.

Is there a way to roll back to the open-source drivers from GRUB and possibly do an update if II'm connected to the Internet via ethernet cable??

**EDIT:** So at the black screen, I pulled up terminal by using "ctrl"+"alt"+"f1" and I did ```
 sudo lshw -C video
``` and found out my graphics are BeaverCreek (Radeon HD 6620G). What is the command to roll back to the open-source drivers?
[B]
EDIT 2: [/B]I was able to fix the problem myself. I was able to use terminal and input: ```
sudo apt-get remove fglrx-updates
``` The next time I booted up, I was working!

---

