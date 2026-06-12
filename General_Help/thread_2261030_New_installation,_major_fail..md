---
title: "New installation, major fail."
date: 2015-01-15
forum: General Help
---

### Post by garpt01 on 2015-01-15
Hi guys/ gals,
  Just installed new 14.04 Studio last week after 11.04 was getting a bit old in the tooth. I've been personalizing some things, and added a new start up sound file tonight. When I rebooted,  got the error: "Screen, graphics card and input device could not be detected properly". Then I get the low resolution mode warning, but I can't get into the system, that it where it freezes. 
  I know just enough to be dangerous with Linux/ Ubuntu, and I *was* in root when I changed the sound file. Don't know if I did something (didn't exit root?). I tried all the relevant recovery options. I need to do something from root prompt (I hope!) . It is a dual boot system, I can't afford to lose windows which is still fine.

 Could someone please help me with some options? 

Thanks for ANY assistance! (almost had 14.04 set up perfectly for me!)

---

### Post by ubfan1 on 2015-01-16
Try the grub options and select a recovery choice for the latest kernel.  Or try editing in the "nomodeset" option yourself on your current grub choice.  Then take a look at "Additional Drivers" from the Dash, and see if any proprietary video drivers are offered.

---

### Post by garpt01 on 2015-01-16
Thanks for the reply. 

Tried the previous grub. Can't get to any dash. I will try this (link) tonight, I'm getting near the end and may just have to reinstall: 

[http://unix.stackexchange.com/questions/98622/how-to-repair-ubuntu-after-upgrade-from-recovery-mode](http://unix.stackexchange.com/questions/98622/how-to-repair-ubuntu-after-upgrade-from-recovery-mode)

or this:

[http://blog.technotesdesk.com/ubuntu-12-4-the-system-is-running-in-low-graphics-mode/](http://blog.technotesdesk.com/ubuntu-12-4-the-system-is-running-in-low-graphics-mode/)

---

### Post by efflandt on 2015-01-16
What graphics card/chip do you have? For Nvidia you usually need to set **nomodeset** while booting a live/install system (hit any key when you see keyboard/mouse symbols at bottom) before installing and that will carry over into grub settings for installed system.

You do not give details about what you were trying to alter or which video drivers you may have tried to install, so we do not know what you might need to undo or if it is just due to kernel modesetting that nomodeset might fix. I had trouble installing 14.04 because the initial nvidia-current driver was too old for my new GTX 750 Ti. And I could not get into any of the text consoles from there (Ctrl+Alt+F1, etc.) because when I tried to log into those, they just flashed the motd for an instant and returned to login prompt. Although, since purging/installing newer nvidia drivers from a recovery boot (which would hang for a while trying to bring up networking due to unrecognized hardware error) everything now works fine.

---

### Post by garpt01 on 2015-01-16
Hi efflandt,
  Thanks for the response.  have ATI Radeon 4600 series, I believe, in firewire (dual card) setup. Older, but still performs well by today's standards. I read about all the ATI issues/ fixes with the error mentioned. No go. I really bork'd something but good!  I'm in the process of setting up a new install right now, on a brand new hard drive. I would really like to install the proprietary drivers so I can control clocking and other settings but just missed support for those cards. 
Better luck this time I hope. 11.04 Studio lasted me more then 3 years basically trouble free. 
Thanks!
-Gary

[COLOR=#DD4814][COLOR=#000000]
[/COLOR][/COLOR]

---

### Post by Bucky Ball on 2015-01-16
*Thread moved to **General Help**.*

Dash is a Unity thing. UStudio uses xfce4 desktop manager. Think Xubuntu. ;)

You didn't try 'nomodeset', as suggested, before deciding to reinstall?

---

### Post by garpt01 on 2015-01-16
I installed dash on top so I get the studio apps I want/ need (but prefer Unity. Guess I'm weird.). 
Tried nomodeset. It was an older HD, started with minor boot issues, so best way to go IMO was to start fresh with a new install/ HD before I got too invested in things.

---

### Post by Bucky Ball on 2015-01-16
All good. Perhaps post a new thread with a descriptive title for any issues you have with the new install, unless it turns out to be the same issue, which is unlikely, but possible! ;)

---

### Post by garpt01 on 2015-01-16
Thanks, Bucky B
  I'm marking this solved. Everything appears good. Now back to customization....:eek:

---

### Post by Bucky Ball on 2015-01-16
All good and good luck with it. ;)

---

