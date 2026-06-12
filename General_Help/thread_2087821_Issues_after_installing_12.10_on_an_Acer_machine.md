---
title: "Issues after installing 12.10 on an Acer machine"
date: 2012-11-24
forum: General Help
---

### Post by Tabb on 2012-11-24
Hi all,

so i decided to take the plunge and format my 5 year old PC and install ubuntu (I had Vista Home premium on before)

I have never had problems with vista, just i felt it was getting slightly slower and i was to clean the bad boy out. 

So installed 12.10, everything went well, but i'm having some issues now that i can't ignor.

#1
When u turn the computer on, the acer welcome screen comes on but then the screens (i have 2) go black and the monitor goes to sleep. However! If i then unplug the machine then plug it back in (i know thats not good) Ubuntu will load and the thing starts up fine. Weird??

#2 
After browsing (On Firefox) for awhile, if itry to load pages to quickly or load multiple programs up the thing freezes on me, and i have not idea why. any ideas?

I really need some help here as i want to use Ubuntu but i'm being driven away by the fact that Vista never failed me and Ubuntu is going on me right out the gates.

Here's my pc details:
Acer M5620
Processor: Intel Core2 Quad Q6600 (2.4GHz)
3GB RAM
32-bit
Thanks All!

---

### Post by Futant on 2012-11-24
Perhaps your machine is too old to handle Ubuntu 12.10? You could try installing Lubuntu, it's a lot easier on older hardware...

---

### Post by mlentink on 2012-11-24
> **Futant said:**
> Perhaps your machine is too old to handle Ubuntu 12.10? You could try installing Lubuntu, it's a lot easier on older hardware...

A quad core with 3GB memory? Nah...

Tabb: any particular reason why you didn't install the 64 bits version?

And could you provide specifics on your graphics hardware? Not that I have a clue on the cause of your monitor issue, but it could have something to do with the drivers.

---

### Post by Futant on 2012-11-24
Twas just a thought :P

---

### Post by Tabb on 2012-11-25
I have an Nvidia GF108 [GeForce GT 430] Rev a1

This is what i get when i type the following command into terminal
(under VGA compatible controller)

[HTML]$ lspci
 $ lspci -v
 $ lspci -v | less[/HTML]

So a new problem has emerged when i click on 'Dash Home' button the computer freezes

Thanks

---

### Post by Tabb on 2012-11-25
And also the orginal Vista running on the machine was 32-bit, so i assumed it was a 32-bit computer. 

One more thing, the Graphics Card i installed as an add-on

---

### Post by personalpc on 2012-11-25
ok the black screen is either grub displaying on the onboard card(if it has one) or it just can't recognize the monitor. Add vga=771 to boot options

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

the failing in firefox and the lag is most likely proprietary drivers not installed

ctl+alt+F1 and login to the terminal with your username & password

This command will install the gnome fallback that will use basic video drivers:

sudo apt-get install gnome-session-fallback


This will reboot your computer

sudo shutdown -r now


once it comes back up you will see a circle to the right of your login name click that to access the drop down menu and select gnome classic no effects. you should be able to move around pretty quick in there. 

Once you are there go to applications -> system tools -> system settings

click on software sources  then check all the boxes on the Ubuntu Software Tab and also on the Other Software tab. 

Finish up with an update and it should grab the nvidia mods if not then run jockey-gtk or jockey-text from terminal found in the repos. Cheers!

---

