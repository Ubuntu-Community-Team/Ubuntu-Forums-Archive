---
title: "X randomly crashes"
date: 2008-01-21
forum: General Help
---

### Post by zhimsel on 2008-01-21
Hey forums,

I'm using Gutsy with the nvidia-glx-new driver. For some reason, X crashes at random intervals. It's alway when I click on something (be it Firefox, a panel menu, desktop icon, etc) and X always restarts after (almost as if I hit ctrl+alt+backspace). As far as I can tell there's nothing in the logs (maybe I'm looking in the wrong place, I don't know). I did recently replace my video card (the old on was ATI), but have successfully switched drivers and reconfigured X. I can't remember if this problem was also occurring before the video card switch or not. But I don't think it did. Does anyone know of this problem, or a fix for it?

P.S. I want to that everyone on the forums who has helped me in the past. I'm not necessarily new to Linux, but I wouldn't call myself an expert. Thus I am usually not much help to others. I usually try to give back to communities I am involved in, but there's not much I can do here. I feel like I have been leeching a bit off you guys and I want to thank you. I will try my best in the future to help on any topics I am proficient in.

---

### Post by erpo on 2008-01-22
> **zhimsel said:**
> Hey forums,

I'm using Gutsy with the nvidia-glx-new driver. For some reason, X crashes at random intervals. It's alway when I click on something (be it Firefox, a panel menu, desktop icon, etc) and X always restarts after (almost as if I hit ctrl+alt+backspace). As far as I can tell there's nothing in the logs (maybe I'm looking in the wrong place, I don't know). I did recently replace my video card (the old on was ATI), but have successfully switched drivers and reconfigured X. I can't remember if this problem was also occurring before the video card switch or not. But I don't think it did. Does anyone know of this problem, or a fix for it?

P.S. I want to that everyone on the forums who has helped me in the past. I'm not necessarily new to Linux, but I wouldn't call myself an expert. Thus I am usually not much help to others. I usually try to give back to communities I am involved in, but there's not much I can do here. I feel like I have been leeching a bit off you guys and I want to thank you. I will try my best in the future to help on any topics I am proficient in.

The quick solution is probably to reinstall the OS. Otherwise, check /var/log/Xorg.0.log for useful information.

---

### Post by zhimsel on 2008-01-22
> **erpo said:**
> The quick solution is probably to reinstall the OS. Otherwise, check /var/log/Xorg.0.log for useful information.

I would rather not reinstall... (ugh!) I've attached my Xorg.0.log. I looked through, but I couldn't find any errors or whatnot. And on a sidenote, the date on the log is from 5 days ago...

---

### Post by torea on 2008-01-24
I'm getting the same crash (similar results than using ctrl+alt+backspace) with Feisty and an nvidia card.
I get the problem when trying to access some websites (with flash animations inside probably) using firefox. 
[http://www.adobe.com/support/](http://www.adobe.com/support/) results in a X reboot all the time for example.
I also get the problem when clicking on the "OpenGL/GLX information" item in the nvidia X server settings program. I can access all other items without problems..

any clue how to solve this?

---

### Post by zhimsel on 2008-01-24
> **torea said:**
> I'm getting the same crash (similar results than using ctrl+alt+backspace) with Feisty and an nvidia card.
I get the problem when trying to access some websites (with flash animations inside probably) using firefox. 
[http://www.adobe.com/support/](http://www.adobe.com/support/) results in a X reboot all the time for example.
I also get the problem when clicking on the "OpenGL/GLX information" item in the nvidia X server settings program. I can access all other items without problems..

Mine seems to be more random, but sounds like the same crash to me. Another friend seems to be having the same problem as well. He is running feisty (but with everything manually installed from gutsy, i.g. compiz, etc)

---

### Post by torea on 2008-01-24
actually, I got a temporary solution for my problem.
I tried to install the nvidia-glx-new package from the synaptic package manager and reboot my computer.
The glx driver seems not to be recognized so I cannot use glxgears for example, but at least I don't have this crash anymore (not yet?).

--
edit:
I just got a real solution by uninstalling the driver and do a manual install of the new driver 169.09 using Envy. glx works and no crash encountered yet!

---

### Post by Kzin on 2008-02-26
I am getting the same crash, gutsy, using restricted driver for my nvidia card, using cube desktop switching and wobbly windows.
Random X reboot seems to happen when I press the minimize button on firefox.  Not every time, but sometimes.  Anyone know where I could look for logs other than xorg that could potentially have relevance?

---

### Post by AdNZL on 2008-02-27
> **Kzin said:**
> I am getting the same crash, gutsy, using restricted driver for my nvidia card, using cube desktop switching and wobbly windows.
Random X reboot seems to happen when I press the minimize button on firefox.  Not every time, but sometimes.  Anyone know where I could look for logs other than xorg that could potentially have relevance?

That's the exact description of the problem I have. The crash is almost instant, just like hitting Ctrl-Alt-Backspace, and only seems to happen when I hit the minimise button on firefox, but sometimes doesn't happen for weeks, then "BAM! WFT?! Doh" :( Not a major problem so far but definitely annoying, as apart from two lock up's I've had recently ( think it might be more of a hardware fault than software) my sytems been as solid as a very solid rock. :guitar:

I have a feeling this is going to be one of those problems that is just to damn hard to track down and fix :(

---

### Post by Kzin on 2008-02-27
Yea will be a tough one to crack... As torea pointed out, it could be a driver issue as well.  I wonder, do you know if you also have an nvidia chipset on your mobo?  I've got nForce4.  Something else to note would be I am generally listening to music when it happens, using Rhythmbox.  Perhaps if we can figure out the commonalities???

---

### Post by zhimsel on 2008-02-27
I haven't had X crash in a while, but if I can remember correctly, it happened quite randomly. It seemed to happen with some interaction with Firefox more often than not; but it also happened when interacting with gnome-panel and others as well.

---

### Post by AdNZL on 2008-02-29
Oh yeah I forgot to mention my graphics card is an Nvidia FX5200 :) Seems to be a reoccurring theme, or could it be that most Ubuntu users prefer to use Nvidia???

---

### Post by c_plus_plus on 2008-03-10
I seem to have the same problem. Common denominators: Firefox minimize, Compiz Fusion, nVidia-GLX driver. Ill try replicating the error and getting you the log asap.

---

### Post by knives on 2008-04-27
I have only just finished setting up Gutsy, I have a radeon 9550, and I seem to be getting the same problem. Firefox, RythmBox, Pidgin all running, but when I do things in firefox, X restarts.
I have only JUST (last 12 hours) finished getting the ATi restricted drivers to work properly, had to edit xorg.conf to get 1280x1024 resolution, now its working this happens (x restarting).
Has there been any progress on finding out what is causing this wonderful problem?

---

### Post by JeffVanderkooij on 2008-05-27
I have the same problem. I'm using a Vaio laptop, I think it uses an Intel integrated graphics card. It just happened to me, while running two FF windows probably 20 something tabs between them, no media(ie videos, music). It seems to happen when the CPU is in high demand. Possibly from a memory leak in FF. So if I remember to keep an eye on the system monitor, it doesn't happen. I haven't found a solution to this yet, I had the problem since I switched to Gutsy. 
Symptoms:
Computer has been booted up for more than two hours
High CPU usage
minimize firefox
Acts like I had hit Ctrl+Alt+Backspace
Severe annoyance ensues :)  
There is a Xorg log error, gdm xioerror fatal errer

---

