---
title: "Update to Ubuntu 15.10 : Usb pendrives not mounting, Display settings not saved. Poli"
date: 2015-11-11
forum: General Help
---

### Post by akshay-sulakhe on 2015-11-11
2 days before I upgraded by system from Ubuntu 15.04 to Ubuntu 15.10 and I hope I don't come to regret it.  Hardware specs : Intel 2600k, Asrock Mobo, 16gb Dddr3 ram, Graphics card : Nvidia Gtx 560ti.  Software specs : Ubuntu 15.10 desktop X64. 
  The problems are as follows :
  
[LIST=1]
[*]Whenever I start my desktop, the display settings are out of whack,  only one monitor is working, other one is flickering. I have to first  disable that monitor in display, re-enable it, save it, then move  monitor in right position, then save it. This is the only sequence which  works and I don't wanna follow it everyday ritualistically.
[*]As soon as the system starts, I get a prompt to ask password, and  even if I enter it, the prompt keeps coming back like ads, until I give  the command below. Also, until I enter the password, I cannot see the  mouse pointer. I don't understand what both have got to do with each  other.
[*]USB pendrives are seen in Nautilis, but cannot be mounted. Even if I  open as sudo nautilus, then ubuntu shows me nothing in the drive. Tried  working 2 different drives.
[/LIST]
  Command which kills password prompt :


```
 sudo killall polkit-gnome-authentication-agent-1
```

Any help with these 3 issues would be nice. Thanks a lot. :-)

---

### Post by Smask on 2015-11-11
> **akshay-sulakhe said:**
> The problems are as follows :
  
[LIST=1]
[*]Whenever I start my desktop, the display settings are out of whack,  only one monitor is working, other one is flickering. I have to first  disable that monitor in display, re-enable it, save it, then move  monitor in right position, then save it. This is the only sequence which  works and I don't wanna follow it everyday ritualistically. 
[/LIST]
 
Do you use Gnome Flashback? If so, look at my last post in the thread [http://ubuntuforums.org/showthread.php?t=2300563&p=13385458#post13385458](http://ubuntuforums.org/showthread.php?t=2300563&p=13385458#post13385458) for a possible workaround.

---

### Post by akshay-sulakhe on 2015-11-11
And what is the workaround, I cannot find any settings information which is mentioned in that thread.

---

### Post by Smask on 2015-11-11
> **akshay-sulakhe said:**
> And what is the workaround, I cannot find any settings information which is mentioned in that thread.

Run gnome-control-center, wihich are the Gnome version of System Settings, select Displays. Click Arrange Combined Displays (The Ubuntu variant is so much easier to use...)

---

### Post by akshay-sulakhe on 2015-11-11
I have Unity, not Gnome. Also, when I ran gnome-control-center, it opened up UBuntu-settings page. In that, in Displays, there is no option to 'Arrange combined displays'. Screenshot URL : [http://postimg.org/image/iqir5k78h/](http://postimg.org/image/iqir5k78h/) [IMG]http://postimg.org/image/iqir5k78h/[/IMG]

---

### Post by Smask on 2015-11-12
> **akshay-sulakhe said:**
> I have Unity, not Gnome. Also, when I ran gnome-control-center, it opened up UBuntu-settings page. In that, in Displays, there is no option to 'Arrange combined displays'. Screenshot URL : [http://postimg.org/image/iqir5k78h/](http://postimg.org/image/iqir5k78h/) [IMG]http://postimg.org/image/iqir5k78h/[/IMG]

???

[ATTACH=CONFIG]265517[/ATTACH][ATTACH=CONFIG]265516[/ATTACH]

---

### Post by akshay-sulakhe on 2015-11-12
Did you see the screenshot? The options you described are not available in settings. And the images you have added, the display settings I have doesn't look like this.

---

### Post by Smask on 2015-11-12
> **akshay-sulakhe said:**
> Did you see the screenshot? The options you described are not available in settings. And the images you have added, the display settings I have doesn't look like this.

Your screenshot looks like it's taken from unity-control-center. In flashback, gnome-control-center install itself as "Settings", compared to u-c-c "System Settings". If you are unsure, start the program from a terminal.
 The point still stands that my first post was if you ran gnome flashback, but since you're not, the workaround may not be for you.

---

### Post by akshay-sulakhe on 2015-11-12
I don't run gnome flashback, and when I gave the command you had suggested, it started the Unity System settings... :-(

---

