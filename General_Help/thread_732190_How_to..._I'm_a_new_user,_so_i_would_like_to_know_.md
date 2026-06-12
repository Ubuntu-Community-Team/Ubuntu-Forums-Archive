---
title: "How to... I'm a new user, so i would like to know how"
date: 2008-03-22
forum: General Help
---

### Post by ultimatebuster on 2008-03-22
So I'm new to Ubuntu. I used Wubi so i could boot into both system. I've got some problems with my ubuntu operating system:

1. I do not know how to install anything. I tried to install OpenOffice.org 2.3. When i unextracted it and click the setup thing. It gives me a pop-up window and saying something about executable text file.

2. My current monitor is 1280x768, but there is no such option. And it is very annoy everytime I boot into Ubuntu the monitor will say Input Not Supported before it auto configs. And same thing when exiting Ubuntu and go to Windows.

3. I still don't have any driver installed. I went to the computer's driver page, but there is only Windows XP driver on it. My computer model is: **HP Pavilion a1120n**

Thanks,

---

### Post by jken146 on 2008-03-22
> **ultimatebuster said:**
> 1. I do not know how to install anything. I tried to install OpenOffice.org 2.3. When i unextracted it and click the setup thing. It gives me a pop-up window and saying something about executable text file.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

Those two links will explain things.  Ubuntu (the standard version) comes with OpenOffice 2.3 installed already.

> 2. My current monitor is 1280x768, but there is no such option. And it is very annoy everytime I boot into Ubuntu the monitor will say Input Not Supported before it auto configs. And same thing when exiting Ubuntu and go to Windows.
OK, follow these steps:
First, press Ctrl+Alt+F1 and log in.  You won't see any asterisks for your password but don't worry.  Then type ```
 sudo /etc/init.d/gdm stop
``` then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and pick your desired resolutions.  Next, ```
sudo /etc/init.d/gdm start
``` should bring you back the graphical log in screen.

> 3. I still don't have any driver installed. I went to the computer's driver page, but there is only Windows XP driver on it. My computer model is: **HP Pavilion a1120n**
Driver for what?  If a piece of hardware works, this means you are already using a driver for it.  Some things (like some graphics cards and some wireless cards in particular) will have proprietary drivers available, but these will not be in use by default.  Go to System -> Administration -> Restricted Drivers Manager to see if there are any.

---

### Post by pointone on 2008-03-22
OpenOffice.org is installed by default in Ubuntu. Secondly, to install any application, you should stick to Ubuntu's package management system unless there's some reason you need another solution. Read [this]("https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html").

Most hardware is supported well by Ubuntu out of the box. The only hardware that really needs special driver installation are video cards and wireless NICs. These drivers are usually available through the "Restricted Drivers Manager" in the System > Administration menu.

*EDIT* Beat to the punch! Bah!

---

### Post by edm1 on 2008-03-22
Edit: Got beaten to it

1) OpenOffice is already installed. Check under Applications>Office. You can't  install exe files. They are made for windows and so will not work in linux. The normal way to install software is by the 'Add/Remove...' or 'Synaptic' applications or by downloading and executing an ubuntu compatible deb file.

3) What drivers do you need specifically? Ubuntu comes preloaded with lots of generic drivers for all types of hardware.

---

### Post by tvtech on 2008-03-22
installing things is easy

get yourself an internet connection

go to 

Applications> Add Remove> now select the type of program you may want to install.  

want to install windows programs?  albeit with limmited success?  

install wine

[http://www.winehq.org]("http://www.winehq.org")

also check out 
[http://www.sourceforge.net]("http://www.sourceforge.net")
always a great source for open source.

do a little searching on google most programs have precompiled.  .deb installer packages built for them somewhere.  it might just take a minute to find.

---

### Post by jken146 on 2008-03-22
> **pointone said:**
> *EDIT* Beat to the punch! Bah!

;)

---

### Post by ultimatebuster on 2008-03-22
> **jken146 said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

Those two links will explain things.  Ubuntu (the standard version) comes with OpenOffice 2.3 installed already.


OK, follow these steps:
First, press Ctrl+Alt+F1 and log in.  You won't see any asterisks for your password but don't worry.  Then type ```
 sudo /etc/init.d/gdm stop
``` then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and pick your desired resolutions.  Next, ```
sudo /etc/init.d/gdm start
``` should bring you back the graphical log in screen.


Driver for what?  If a piece of hardware works, this means you are already using a driver for it.  Some things (like some graphics cards and some wireless cards in particular) will have proprietary drivers available, but these will not be in use by default.  Go to System -> Administration -> Restricted Drivers Manager to see if there are any.

For the second one, I somehow did nothing to the screen. there is a whole lot of text of warning or something like that. and backup stuff.

For the third one, I think the sound card is not working cz every sound i hear did not came from the speaker, rather somethig else. 

By the way, Since I installed wubi, it only gives me OpenOffice 2.2, so i like to upgrade

---

### Post by jken146 on 2008-03-22
> **ultimatebuster said:**
> For the second one, I somehow did nothing to the screen. there is a whole lot of text of warning or something like that. and backup stuff.
Check again in the screen resolution settings (under System -> Preferences).  What graphics card are you using?

> For the third one, I think the sound card is not working cz every sound i hear did not came from the speaker, rather somethig else. 
Where does it come from?  [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) is the sound section of the Ubuntu documentation.  The first thing I would try is using alsamixer to check that the volume is turned up (search for that, you should find an explanation easily).

> By the way, Since I installed wubi, it only gives me OpenOffice 2.2, so i like to upgrade
Which version of Ubuntu did you install?  If you don't know, type ```
cat /etc/lsb-release
``` to find out.

---

### Post by ultimatebuster on 2008-03-22
7.04, that is my version of Ubuntu

---

### Post by jken146 on 2008-03-22
You should upgrade to 7.10.

---

### Post by ultimatebuster on 2008-03-22
> **jken146 said:**
> You should upgrade to 7.10.
I can't, at least i don't wubi allows it. So how do I upgrade my OpenOffice to 2.3?

And My screen is wide screen. I need it to be 1280x768.

---

### Post by ultimatebuster on 2008-03-22
Sorry to double post, but is there any one to help?:(:confused::confused::confused::confused:

---

### Post by edm1 on 2008-03-23
The newest version is included in ubuntu 7.10. [Follow this guide to upgrade.]("https://help.ubuntu.com/community/GutsyUpgrades#head-bcde2981ccb8812c84887606459e2df030ef2c34")

---

### Post by S.Milo on 2008-03-25
Quote:
OK, follow these steps:
First, press Ctrl+Alt+F1 and log in.  
You won't see any asterisks for your password but don't worry.  

Then type:

 ```
 sudo /etc/init.d/gdm stop
``` then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and pick your desired resolutions.  Next, ```
sudo /etc/init.d/gdm start
``` should bring you back the graphical log in screen.

End QUOTE

Where do I type this code?  I cannot get a screen resolution larger than 600x800, therefore things are getting cut off... Everything is too big!  I think this code will help, I just need to know where I can type it.  Thanks!

P.S.  I'm very new to Linux / Ubuntu, and I'm running GNOME on a Compaq Armada.

---

### Post by eriqjaffe on 2008-03-25
> **S.Milo said:**
> Quote:
OK, follow these steps:
First, press Ctrl+Alt+F1 and log in.  
You won't see any asterisks for your password but don't worry.  

Then type:

 ```
 sudo /etc/init.d/gdm stop
``` then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and pick your desired resolutions.  Next, ```
sudo /etc/init.d/gdm start
``` should bring you back the graphical log in screen.

End QUOTE

Where do I type this code?  I cannot get a screen resolution larger than 600x800, therefore things are getting cut off... Everything is too big!  I think this code will help, I just need to know where I can type it.  Thanks!

P.S.  I'm very new to Linux / Ubuntu, and I'm running GNOME on a Compaq Armada.Ctrl+Alt+F1 brings you to a virtual terminal (think of it as the Linux equivalent of a DOS prompt), and that's where you enter all those commands.

---

### Post by S.Milo on 2008-03-25
I've done everything in the virtual "DOS" type thing,

The screen reads:

* Starting GNOME Display Manager...   
                                                        [ OK ]

but it doesn't seem to be doing anything.

Any advice?

---

### Post by pointone on 2008-03-25
Press Ctrl+Alt+F7 to return to the GUI.

---

