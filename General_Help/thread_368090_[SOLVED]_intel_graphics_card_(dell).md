---
title: "[SOLVED] intel graphics card (dell)"
date: 2007-02-22
forum: General Help
---

### Post by Homunculi on 2007-02-22
i have everything running on my main system (non dell) excellent beautiful install and running nice :guitar: 

i have a computer that my son uses and i tried to install a kde desktop for him 
turn out that the system has a integrated intel graphic card for the primary display 

does anyone have any suggestions as to how to get the intel card to work 
hew only needs the computer for educational games and school 

we are looking at getting rid of windows from the entire house ... to much $$ invested for all the headaches it has caused 

if anyone has any help or a workaround   that would get it to work i am all ears :popcorn: 

733 celeron 
64mb ram 
20gb hard disk 
intel graphics 
sound unknown 
10/100 3com

---

### Post by slackware on 2007-02-22
Do you know the exact model of the onboard graphics? And if it's possible, I would definitely upgrade the ram.

---

### Post by Homunculi on 2007-02-22
sorry ... 
intel 82810-dc100 graphics controller

---

### Post by slackware on 2007-02-22
What happens when you attempt to install KDE? Any specific error messages? What shows up in the xorg log? The log file is located in /var/log/

---

### Post by Homunculi on 2007-02-22
nothing ... locks up and will not continue

but what can i say for a 15 dollar computer

---

### Post by slackware on 2007-02-22
Have you tried installing a light weight window manager like Fluxbox instead of a full Desktop enviroment? Maybe go with a barebones install and add the packages you need from there.

---

### Post by Homunculi on 2007-02-22
will give it a try ... thank you .. 
and i will let you know ... xfce or flux

---

### Post by Homunculi on 2007-02-23
well nope still locks up  in graphics mode ...

---

### Post by mbeierl on 2007-02-23
Please post the contents of your /etc/X11/xorg.conf file.

I've got ubuntu running on my kids' pc with an intel 82865G graphics controller and it works fine.

Excerpt from my xorg.conf:
```

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "NEC LCD1545V"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
Also, if there is anything in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old, please post that too.

You'll probably need to start in 'recovery mode' to get these logs from the command line.

---

### Post by nick.inspiron6400 on 2007-02-23
What Dell?

---

### Post by Homunculi on 2007-02-23
the system will not boot past the splash screen ... 
locks up sites there for and hour or better (i left it to sit to see if it would load ) 
:confused: 

i would post the xorg.conf if there was one to post ..

---

### Post by featherking on 2007-02-23
it should be located in /etc/X11/xorg.conf

---

### Post by chalex on 2007-02-23
It is not clear to me that the problem is only with the graphics.

Have you run memtest?  Have you run the cd media check?  Have you tried the safe VGA mode?

Intel graphics should not be a problem in this case.

---

### Post by Talon2 on 2007-02-23
> 
does anyone have any suggestions as to how to get the intel card to work 


What is the problem?  And what is the chipset?

> 
hew only needs the computer for educational games and school 

 
My kids really enjoy Edubuntu.

> 
64mb ram


Ummm... this is a problem.  I have two P3 boxes (700 and 750mhz) that do well with Xbuntu and Ubuntu but these boxes have 512mb of ram.  I'll offer the opinion that it could be hard to track down exactly what the problem is on a machine with this small amount of ram.  I doubt that *unbuntu is tested on systems below the required minimum amount of ram so you may have a video problem but then again, you may not.

---

### Post by Homunculi on 2007-02-24
i have run the memtest and it is ok .. no errors 

i have not ever started a ubuntu cd (xubuntu for xfce ) in vga safe mode before 
if you have the instruction please post and once i get there i will have my fingers crossed 
______

if all els fails i can get an upgrade and pass my system down to him 

do not think it is buyer beware .. i bought the entire system for $15 dollars if it does not work it does not work ... no harm no foul but the darn thing runs windoze 98SE

](*,)

---

### Post by mbeierl on 2007-02-26
My router box at home is running Ubuntu with Gnome desktop, and it's got 128M of ram.  Seems to work well enough.  But as far as lockups go, I doubt insufficient ram would do that.

Are you just running livecd or is it actually installed?

---

### Post by Homunculi on 2007-02-26
well i went to ther flea market and got another system for 20 bucks .... 
believe it or not .. gateway with a intel video chipset .... :( 

so i talked to the wife and i am getting a upgrade for my computer and giving my 10 year old a p4 2.8 with 1gb ram .... 

wish i had a dad like me tho :) 

darn lucky kid ... and my oldest just moved out too  :-k 

i will give him one of the other systems .... 
thank you for all the help and points to try .. .... 

and when i get my upgrade ... the young one will get my system

---

