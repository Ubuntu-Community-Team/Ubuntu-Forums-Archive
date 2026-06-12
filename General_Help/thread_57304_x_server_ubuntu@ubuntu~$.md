---
title: "x server/ ubuntu@ubuntu:~$"
date: 2005-08-16
forum: General Help
---

### Post by natural on 2005-08-16
Ok now. After i go through all of the install stuff, testing/scanning...i get this popup 

[img]http://xs42.xs.to/pics/05332/DSC00148.JPG[/img]

After that it loads a little more then it stops and i have this

[img]http://xs42.xs.to/pics/05332/DSC00149.JPG[/img]

Up a little more it says 

' **_This Processor " Intel(R) Celeron(R) CPU 2.20Ghz is known _not_ to support power-saving. _**'


I dont know why but it just stops and says " ubuntu@ubuntu:~$ "

I made a very small, crappy compressed video of another error i found.
[http://www.sasfilms.com/video/9726-mov00150.mpg](http://www.sasfilms.com/video/9726-mov00150.mpg) 


If you could help me at all i would appericate it, i backed all my stuff up for hours and i wanna get this thing running. Thanks ahead.

---

### Post by codejunkie on 2005-08-16
it's not setting up your video card correctly usualy a quick fix to that is 
```
sudo dpkg-reconfigure xserver-xorg
``` and in the first section choose [SIZE=2]vesa[/SIZE] as the driver and answer hit enter through the rest of the setup questions it should set the right values for you and reboot. also if you have more than one video card installed in the same machine like onboard video and an add on video card make sure the onboard video is disabled because this can cause conflicts let me know if this helps.

---

### Post by natural on 2005-08-16
is that code you sent just one command line? yeah i have a stupid onboard chip and i have a pci graphics card. the onboard one should be disabled though.

" and in the first section choose vesa as the driver "

i was never prompted what driver to use...does it prompt me after i do the sudo code?

---

### Post by codejunkie on 2005-08-16
[QUOTE=natural]is that code you sent just one command line? yeah i have a stupid onboard chip and i have a pci graphics card. the onboard one should be disabled though.

" and in the first section choose vesa as the driver "

i was never prompted what driver to use...does it prompt me after i do the sudo code?[/QUOTE]
yes that code is just one command but make sure you have that onboard video completly disabled in the bios onboard video caused me three weeks of headaches until i figured it out on mine if you don't disable it you have to manually edit the /etc/X11/xorg.conf file know exactly what the pci bus id the card is using, card model name etc and add it all by hand.

---

### Post by natural on 2005-08-16
haha yeah that would be bad. yeah i just checked and its disabled. im about to try now hopefully your advice works.

I'll post back the status. thanks for the reply's

---

### Post by natural on 2005-08-16
Well. 

I did the command, selected versa and went through setting up all the mouse/keyboard/ and everything else. then i came to the last screen that asked what bit-color i wanted and i hit enter which was 24 bit (which my monitor supports).

Then it just showed this.

[IMG]http://xs42.xs.to/pics/05332/DSC00151.JPG[/IMG] 

the command line once again said " ubuntu@ubuntu:~$ "

So, i tried rebooting and it looked exactly the same with the same CPU error

---

### Post by codejunkie on 2005-08-16
[QUOTE=natural]Well. 

I did the command, selected versa and went through setting up all the mouse/keyboard/ and everything else. then i came to the last screen that asked what bit-color i wanted and i hit enter which was 24 bit (which my monitor supports).

Then it just showed this.

[IMG]http://xs42.xs.to/pics/05332/DSC00151.JPG[/IMG] 

the command line once again said " ubuntu@ubuntu:~$ "

So, i tried rebooting and it looked exactly the same with the same CPU error[/QUOTE]
i didn't notice or think to ask this before but i see you are using the live cd so you can't reboot because it doesnt save any settings to the harddrive it loads files temporarly into ram and clears them when you reboot so i don't know if this will work for sure but it's worth a shot after you run 
```
sudo dpkg-reconfigure xserver-xorg
```
try
```
sudo /etc/init.d/gdm restart
```
that might work but i havent tried it with the live cd.

---

### Post by natural on 2005-08-16
will do, brb.

i should of mentioned i was using the Live CD

---

### Post by natural on 2005-08-16
Ok i did the reconfigure command again. followed by the restart command after its all done and the screen flashes then i get one of the popup's i used to get, butthis time ...it has funky characters around it. 
[IMG]http://xs42.xs.to/pics/05332/DSC00152.JPG[/IMG]
Hit ok..nothing happened. Tried to restart again, same thing.

---

### Post by codejunkie on 2005-08-16
[QUOTE=natural]Ok i did the reconfigure command again. followed by the restart command after its all done and the screen flashes then i get one of the popup's i used to get, butthis time ...it has funky characters around it. 
[IMG]http://xs42.xs.to/pics/05332/DSC00152.JPG[/IMG]
Hit ok..nothing happened. Tried to restart again, same thing.[/QUOTE]

this is just a guess but i think it still has something to do with the multiple video cards and where it's the live cd not being able to properly edit the xorg.conf file i had similar probems with the live cd using multiple video cards and gave up and i tried the install cd it works fine using the install disk with a little manual editing or you could also try removing the pci card and just using the onboard video if thats an option and see how that works sorry i could'nt be more help.

---

### Post by natural on 2005-08-16
Well, im trying to get OS X to run on it so i dont know if using the install option will mess anything up? 

Once i have it up and running im soposte to open a terminal and do

" dd bs=1048576 if=./tiger-x86-flat.img of/dev/hda "  

Im not sure if anybodys successfully installed and gotton the command line to run 

Thanks for your help. 


Anybody else have an answer?

---

### Post by codejunkie on 2005-08-16
[QUOTE=natural]Well, im trying to get OS X to run on it so i dont know if using the install option will mess anything up? Thanks for your help. 


Anybody else have an answer?[/QUOTE]
if that's what your doing chances are that osX won't support your pci video card either it only supports certian card models but from what i've read it is supposed to support almost all intel onboard video chipsets most likey that's what you have anyway so enable the onboard video remove the pci card and try it.

---

### Post by natural on 2005-08-16
yeah i have an Intel Extreme Graphics AGP onboard. But you think using the onboard will ruin the quality of the OS?

---

### Post by codejunkie on 2005-08-16
[QUOTE=natural]yeah i have an Intel Extreme Graphics AGP onboard. But you think using the onboard will ruin the quality of the OS?[/QUOTE]
from what i've read i think the developer kits from apple shipped with just onboard video installed but if your wanting the os to be top quality id wait and get an intel mac because what your trying to install is probably what somebody hacked together and if it just runs you'll be getting lucky.

---

### Post by natural on 2005-08-16
your right. i tried with the onboard and it didnt work. i think it has something to do with the CPU for some reason. cause it just keeps saying it dosent support power saving. i was actually thinking of just switching to linux, but it seems like theres not enough linux version of the programs i use like adobe premiere, AFX, photoshop,dreamweaver.

You think linux is worth switching to.im getting sick of windows.

---

### Post by codejunkie on 2005-08-17
[QUOTE=natural]your right. i tried with the onboard and it didnt work. i think it has something to do with the CPU for some reason. cause it just keeps saying it dosent support power saving. i was actually thinking of just switching to linux, but it seems like theres not enough linux version of the programs i use like adobe premiere, AFX, photoshop,dreamweaver.

You think linux is worth switching to.im getting sick of windows.[/QUOTE]

yes i do think linux is worth switching to it has tons of advantages over windows it's free, no viruses, spyware, or blue screens of death etc in linux. and i think most if not all of the programs that you mentioned are supported through apps like wine wich is free and (crossover office it costs $30 bucks) but well worth it if you want to run windows software in linux easily and there are even opensource/free software in linux that does the same things as the programs you mentioned, and they don't cost hundreds of dollars for one app like photoshop. plus there are thousands of free programs for linux thats another advantage over windows because you have to drop like $20 bucks+ for every program you find for windows. if your fed up with windows like most people as i can see you are by wanting to install OSX on your pc try linux, OSX and Linux are both based on unix they both are more secure than windows and there both solid as a rock, the hardest thing in linux is the install but if your hardware is supported that even takes less time than a normal windows install, and once it is installed it's rock solid. install ubuntu try it for at least a week and dont give up right away like some people do because it takes time to learn a new os and it will amaze you.

---

### Post by natural on 2005-08-17
well thought out response. i was just being told by someone else that tis program lets you use windows app's on linux. 

what version would you recommend? i need to be able to run a network on my houses (LAN) and be able to run editing program as listed above and such.

---

### Post by codejunkie on 2005-08-17
[QUOTE=natural]well thought out response. i was just being told by someone else that tis program lets you use windows app's on linux. 

what version would you recommend? i need to be able to run a network on my houses (LAN) and be able to run editing program as listed above and such.[/QUOTE]
if your were asking about what version of ubuntu i like hoary5.04 it has all the newer packages 
if your were asking about what version of wine use the latest from [www.winehq.org](www.winehq.org)
if your were asking about what version of crossover office 4.2
and if you have a router to share your internet connection between computers things shouldn't be any different with your networking you can use samba to share files between windows mac and linux.

---

### Post by Velox Letum on 2005-08-20
If you're really attached to your Windows programs (I love Photoshop), get VMware Workstation (not free) for Linux and run a Windows install through it. Then any time you feel that niggling to get on Windows and run your favorite software, pop open VMware, start up the Virtual Machine.

---

