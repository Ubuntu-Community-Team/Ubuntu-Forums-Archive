---
title: "Nvidia GeForce installation on ubuntu Help!!"
date: 2008-06-07
forum: General Help
---

### Post by ryclegman on 2008-06-07
Hello,

I have been having a lot of problems with my graphic card. i just got and built a sate of art computer with 4gig or memory, 500 gig Sata h.d., The band new msi board, and MSI Nvidia GeForce N9600GT. I installed Ubuntu and duel booted it with XP. I installed the stuff for windows so it would work.. i went into Ubuntu and tried to see if the graphic card would work and nothing... Iv been all over the internet looking for things that would work... i tried envy, a few terminal things and still nothing..... if any one can help me set this Driver up i would be very happy!   

Ps.. i also tried the system administration and hardware drivers and nothing was there.. i think i need to install something for the driver!!

---

### Post by Unix_Slayer on 2008-06-07
> **ryclegman said:**
> Hello,

I have been having a lot of problems with my graphic card. i just got and built a sate of art computer with 4gig or memory, 500 gig Sata h.d., The band new msi board, and MSI Nvidia GeForce N9600GT. I installed Ubuntu and duel booted it with XP. I installed the stuff for windows so it would work.. i went into Ubuntu and tried to see if the graphic card would work and nothing... Iv been all over the internet looking for things that would work... i tried envy, a few terminal things and still nothing..... if any one can help me set this Driver up i would be very happy!   

Ps.. i also tried the system administration and hardware drivers and nothing was there.. i think i need to install something for the driver!!


Try this post ===>[http://ubuntuforums.org/showthread.php?t=819043&page=2]("http://ubuntuforums.org/showthread.php?t=819043&page=2")

---

### Post by ryclegman on 2008-06-07
Is this for ubuntu terminal... i found this in one one of the reply's.. and plus i dont have that GFX card...


Attention, Attention, please only follow these steps if you are using KDE4. Sorry about the misunderstanding.

---

### Post by Unix_Slayer on 2008-06-07
> **ryclegman said:**
> Is this for ubuntu terminal... i found this in one one of the reply's.. and plus i dont have that GFX card...


Attention, Attention, please only follow these steps if you are using KDE4. Sorry about the misunderstanding.

It works in all X11 programs. Dropping out of KDE4 was my mistake. Do you know how to drop out of your X11 program to term?

---

### Post by ryclegman on 2008-06-07
No i do not.. plus i forgot to tell you that i ran compiz check and it found that my MSI Nvidia was not rendered.... idk what that means but that migh help... i did download the driver but where do i type that other code into? i tried terminal and it said sh: can open file or sum thing like that..:confused:

---

### Post by Unix_Slayer on 2008-06-07
> **ryclegman said:**
> No i do not.. plus i forgot to tell you that i ran compiz check and it found that my MSI Nvidia was not rendered.... idk what that means but that migh help... i did download the driver but where do i type that other code into? i tried terminal and it said sh: can open file or sum thing like that..:confused:

On your start menu.... System ...  Terminal Program.

---

### Post by brigadoon on 2008-06-07
Please look at my post at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

It may help. Good luck.

---

### Post by ryclegman on 2008-06-08
if anyone has an aim to help me with this problem it would be great... still nothing has worked!!!!

---

### Post by Unix_Slayer on 2008-06-08
> **ryclegman said:**
> if anyone has an aim to help me with this problem it would be great... still nothing has worked!!!!

If you follow my instructions in the bottom post I referenced, it will be a sure shot. Forget this KDE, Gnome stuff. Just drop to term out of X11, and follow the instructions.


**[COLOR="Red"]You might want to print this out.[/COLOR]**


[B]Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
[/B]
**[COLOR="Red"]Step 1[/COLOR]**
        **in terminal window**

```
sudo apt-get install build-essential
```

           **Then :**

```
sudo apt-get remove nvidia*
```


**[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]**


[COLOR="DarkOrange"]Step 2[/COLOR]
         **on your keyboard**

**ctrl+alt+backspace**  [B][COLOR="Red"]<==== this is for KDE4 [Use the correct shortcut for your X11]
[/COLOR][/B]
**Wait for the drop out of X11.**

[COLOR="Blue"]Step 3[/COLOR]

**Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver. **

**type :**

```
chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run
``` 

**NVIDIA-Linux-x86-173.14.05-pkg1.run = name of the file you downloaded. If it's different, then make corrections.**


[COLOR="LightBlue"]Step 4[/COLOR]

**type in :**

```
sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```


**Follow directions on the screen.**

[COLOR="Lime"]Step 5
[/COLOR]
[B]Reboot, and you should be good as new. I don't use Envyng, or Compiz. I like a nice clean install of my devices.
[/B]
Good Luck

---

### Post by ryclegman on 2008-06-09
do you know the shortcut to run that x11 cuse i cant find it..:confused:

---

### Post by ryclegman on 2008-06-09
when i runt that chmod i get this

chmod: cannot access `NVIDIA-Linux-x86-173.14.05-pkg1.run': No such file or directory

---

### Post by ryclegman on 2008-06-09
i almost got it when this popped up 

 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Unix_Slayer on 2008-06-09
> **ryclegman said:**
> i almost got it when this popped up 

 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

That's why you need to drop out of X11. Do a search on forums for the correct command. If your using Gnome, your looking for a GDM stop.

---

### Post by Unix_Slayer on 2008-06-09
> **ryclegman said:**
> when i runt that chmod i get this

chmod: cannot access `NVIDIA-Linux-x86-173.14.05-pkg1.run': No such file or directory

It's   chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run
If it doesn't work, try sudo in front of it. You can tell it's executable when you do a ls, and the file is lime green.

---

### Post by ryclegman on 2008-06-09
I tried /etc/init.d/gdm stop in terminal and it basicly rebooted the comp. the i tried it in ctrl alt f1 and typed it there... can you just tell me the way to quit x server?

---

### Post by ryclegman on 2008-06-09
i just tried it again and this came up

ryan@ryan-desktop:~$ /etc/init.d/gdm stop
open: Permission denied
 * Stopping GNOME Display
Manager...                                            
open: Permission denied

---

### Post by ryclegman on 2008-06-09
Ok it installed hurray... now i got a black screen after the ubunut bar goes acrost.... what should i do now????!!??:confused:

---

### Post by Unix_Slayer on 2008-06-09
> **ryclegman said:**
> Ok it installed hurray... now i got a black screen after the ubunut bar goes acrost.... what should i do now????!!??:confused:


How did you know it installed? Did you get the red and blue screen asking you to make choices? Don't worry about it. I will help you fix it.

---

### Post by ryclegman on 2008-06-09
yha there was the red and gren on the top and bottom then it said installed successfuly then it said to reboot i did and then after ubuntu loads its a black screen. i think it might be easier if we talk on aim if you want to u you can email me it.... [email]ryclegman@aim.com[/email]

If you are able to canw e try to fix this tonight

---

### Post by Unix_Slayer on 2008-06-09
> **ryclegman said:**
> yha there was the red and gren on the top and bottom then it said installed successfuly then it said to reboot i did and then after ubuntu loads its a black screen. i think it might be easier if we talk on aim if you want to u you can email me it.... [email]ryclegman@aim.com[/email]

If you are able to canw e try to fix this tonight

I just e-mailed you.

---

### Post by ryclegman on 2008-06-10
I got it all working...... I just didn't do 1 thing but i figured it out!.. everyone with problems follow his guide!

---

### Post by Unix_Slayer on 2008-06-11
> **ryclegman said:**
> I got it all working...... I just didn't do 1 thing but i figured it out!.. everyone with problems follow his guide!

It might not be perfect, but it works. Glad it worked out for you.

---

### Post by ryclegman on 2008-06-17
Ok.... sorry to have to come back but i got a problem a again.... I was working on ubuntu for a while then a window popped up and said updates r avlaible..... so i did them and the restarted the computer... when i came back the desktop effects were gone... but i noticed after or before idk remember .. the nvidia symbol still showed up... i got pissed after a while and descided to screw this... so i reinstalled ubuntu... I know not the best idea.... I got my themes back to the way i like them. i then did the nvidia installer that i did before that did work. But this time i had no such luck. I got the blackj screen and i couldnt get into it execpt through crtl alt f1........ i tryed it a second time and i got the error that my kernel may of been messed up or configuring issues:confused:? Then i reinstalled ubuntu again and did the installer and now i got the message headers werent installed and i already updated everything so i had to of had the linux headers.... then i got that fixed and then i got it installed.. but during installation i got could not get kernel from Nvidia.com:confused: so i had to later re install ubuntu.... I am hesitent to even try it again... but on the other hand i want the desktop effects and cude...... IDK whats wrong with my computer....SOMEONE HELP!! PLEASE....

---

### Post by ryclegman on 2008-06-17
Ok.... sorry to have to come back but i got a problem a again.... I was working on ubuntu for a while then a window popped up and said updates r avlaible..... so i did them and the restarted the computer... when i came back the desktop effects were gone... but i noticed after or before idk remember .. the nvidia symbol still showed up... i got pissed after a while and descided to screw this... so i reinstalled ubuntu... I know not the best idea.... I got my themes back to the way i like them. i then did the nvidia installer that i did before that did work. But this time i had no such luck. I got the blackj screen and i couldnt get into it execpt through crtl alt f1........ i tryed it a second time and i got the error that my kernel may of been messed up or configuring issues? Then i reinstalled ubuntu again and did the installer and now i got the message headers werent installed and i already updated everything so i had to of had the linux headers.... then i got that fixed and then i got it installed.. but during installation i got could not get kernel from Nvidia.com so i had to later re install ubuntu.... I am hesitent to even try it again... but on the other hand i want the desktop effects and cude...... IDK whats wrong with my computer....SOMEONE HELP!! PLEASE....

---

### Post by Unix_Slayer on 2008-06-18
> **ryclegman said:**
> . IDK whats wrong with my computer....SOMEONE HELP!! PLEASE....

When something goes wrong, reinstalling Ubuntu is not the right option. Things can always be fixed. Now you need to start the NVidia installation over from scratch. When the kernel updates, all you need to do is reinstall the NVidia driver again. This will fix the problem. I'm away on business, and I'm answering on my Blackberry. Try the steps from scratch.

---

### Post by p_quarles on 2008-06-19
Moved to Multimedia & Video.

---

### Post by ryclegman on 2008-06-19
i got it figured out .. i used envyng

---

### Post by Unix_Slayer on 2008-06-23
> **ryclegman said:**
> i got it figured out .. i used envyng

Ok... cool. As long as it's working. Just to let people know. There is a new driver out there that fixes some of the complained about problems.

Version: 173.14.09
Operating System: Linux x86
Release Date: June 11, 2008

Release Highlights

    * Fixed aliased font rendering corruption on X.Org server 1.5.
    * Fixed a display corruption problem driving two dual-link DFPs with Quadro FX 1700 GPUs.
    * Fixed a regression that prevented the X driver from starting on some GeForce FX, 6 and 7 mobile GPUs.
    * Fixed a locale-interaction issue in the nvidia-settings X server configuration file parser.
    * Added preliminary support for Linux 2.6.26.


Again.... This warning. If your NVidia driver is working, and you have no issues.... then I would not mess with this one. I'll be testing this new one out this week. If anyone is interested, I will report later.

---

