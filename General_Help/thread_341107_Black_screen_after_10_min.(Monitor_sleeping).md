---
title: "Black screen after 10 min.(Monitor sleeping)"
date: 2007-01-18
forum: General Help
---

### Post by SLIMwoogi on 2007-01-18
Hello. Guys. 
First, I'm sorry about my poor English.

I got a Problem.](*,) 
--------------------------------------------------------------------------------------------------------------------------------------
I'm using Edgy + XGL + Beryl. Everything is OK except this. Every time I do nothing(don't typing or moving mouse) with desktop for 10 min. my monitor become black out. To recover the screen I must type any key or move mouse.  For example, When I watching a movie, screen show me a black screen after 10 min. exactly.  But I can still hear the sound of movie file. Not just watching something. When download something, I got a same problem.  First time I just thought that it's screensaver.  So I configured System >> Preferences >> Screensaver  not to work. ( Uncheck "Activate screensaver when computer is idle")
But this action didn't work.
Next, I configured "System>>Preferences>>Power Management"  never put the screen to sleep.
But this didn't work too.

What's the problem? I got a no idea. Please help me.](*,) 


My Desktop Specification
--------------------------------------------------------------------------------------------------------------------------------------
CPU : AMD Athlon3500+
GPU : ATI Radeon x1650Pro ( installed  ATI Proprietary Linux x86 Display Driver 8.33.6)
RAM : 2GB
OS : Ubuntu Edgy(x86)

---

### Post by tronica on 2007-01-18
well the default screensaver setting is 10mins. Did you choose the blank screensaver?

---

### Post by tribble222 on 2007-01-18
I'm new to this so someone correct me if I'm giving bad advice...but I read somewhere that you can disable the gnome screensaver from ever starting with the following command:

gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

And then restart gnome.  Of course if you want to use the screensaver this won't be a good solution.

---

### Post by wpshooter on 2007-01-18
> **SLIMwoogi said:**
> Hello. Guys. 
First, I'm sorry about my poor English.

I got a Problem.](*,) 
--------------------------------------------------------------------------------------------------------------------------------------
I'm using Edgy + XGL + Beryl. Everything is OK except this. Every time I do nothing(don't typing or moving mouse) with desktop for 10 min. my monitor become black out. To recover the screen I must type any key or move mouse.  For example, When I watching a movie, screen show me a black screen after 10 min. exactly.  But I can still hear the sound of movie file. Not just watching something. When download something, I got a same problem.  First time I just thought that it's screensaver.  So I configured System >> Preferences >> Screensaver  not to work. ( Uncheck "Activate screensaver when computer is idle")
But this action didn't work.
Next, I configured "System>>Preferences>>Power Management"  never put the screen to sleep.
But this didn't work too.

What's the problem? I got a no idea. Please help me.](*,) 


My Desktop Specification
--------------------------------------------------------------------------------------------------------------------------------------
CPU : AMD Athlon3500+
GPU : ATI Radeon x1650Pro ( installed  ATI Proprietary Linux x86 Display Driver 8.33.6)
RAM : 2GB
OS : Ubuntu Edgy(x86)

Try this.

First make sure your sessions automatic saving changes box is checked.

Then set your power management/screen blanking to 3 minutes.  Then set your screensaver to 1 minute and check the box to enable it.  Then wait about 1 minute for the screensaver to kick in and then wait about 2 or 3 more minutes for the screen to go blank.

Then move the mouse to bring the screen back on and then reboot/restart your computer.  When it comes back up go into the screensaver section and uncheck the screensaver function check box but do NOT move the slider.  Then go into the power management section and move your slider to NEVER.  Now see if your screen stay on.  Alway make sure your screen saver slider is set to a number less that the slider for your power management.

Good luck.

---

### Post by pyrforos on 2007-01-23
same problem.. solution didn't work..any other solution guys?It's really  annoying this!I can't see  a movie from my coach!I have to get up every 10 min!

---

### Post by jocko on 2007-01-23
This problem is not because of any screensaver or gnome power management.
It happens when xgl is run as a session on display :1, when all the power management settings you normally find only concerns display :0 (I guess).
This causes xorg to use preset blank, standby and suspend times that can't be changed through gnome-power-preferences.

[COLOR=Blue]**Here's the solution:**[/COLOR] Add these lines to the end of your /etc/X11/xorg.conf:

```
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```

---

### Post by SLIMwoogi on 2007-01-24
> **jocko said:**
> This problem is not because of any screensaver or gnome power management.
It happens when xgl is run as a session on display :1, when all the power management settings you normally find only concerns display :0 (I guess).
This causes xorg to use preset blank, standby and suspend times that can't be changed through gnome-power-preferences.

[COLOR=Blue]**Here's the solution:**[/COLOR] Add these lines to the end of your /etc/X11/xorg.conf:

```
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```



Thank you so much!!!    You are my sunshine.:D  This solution perfectly work to me.
Thank you again.

---

### Post by eooon on 2007-01-31
This didnt help me... any other suggestions :( Same problem as the once above...

---

### Post by Jumbs on 2007-02-15
I have a similar problem, or maybe the same. When watching a video, the screen goes black after a little while.
I am new to linux, so the thoughts of "screens" and "output moduies" are still above me for now.

The code :

> **jocko said:**
> 

[COLOR=Blue]**Here's the solution:**[/COLOR] Add these lines to the end of your /etc/X11/xorg.conf:

```
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```


Helped, but now i have NO screen power off, even after hours. If i change those number will i have the same issue again? I mean i just want it to work right, just not going to screen saver while a vid is on.
VLC has options for which screen to output the video module or something, but i didnt want to mess with something i didnt know (yet). Would messing with those possibly fix the issue?

Thanks

---

### Post by crafter on 2007-07-08
I've made the changes to xorg.conf as specified, without success. Howvere. pressing Cntrl-Alt-Backspace kills the xserver most times, and I am able to log-in again. No need to reboot!

Also, I was fortumate that I had another user session in session cache. Pressing the Ctrl-Alt-F8 buttons repeatedly eventually brought up the switch user screen that I could log in to the second user account, the su to my ownaccount and kill the screensaver process.

Concrete prrof for me that the screensave is the culprit here.

---

### Post by Johnny M on 2008-01-11
Hi - my monitor has started going into power saving mode as soon as I switch on.  I have tried another monitor and it does the same thing - any good ideas?  It had been working fine since we moved to ubuntu and to my knowledge we havent loaded any software but the kids might have done something...

Should I put in the ubuntu start up disk?

If that works should I put in Jumbs code?

Thanks and best Johnny

---

### Post by teejay17 on 2008-01-13
> **jocko said:**
> This problem is not because of any screensaver or gnome power management.
It happens when xgl is run as a session on display :1, when all the power management settings you normally find only concerns display :0 (I guess).
This causes xorg to use preset blank, standby and suspend times that can't be changed through gnome-power-preferences.

[COLOR=Blue]**Here's the solution:**[/COLOR] Add these lines to the end of your /etc/X11/xorg.conf:

```
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```
I tried this because I had the same problem. It worked like a charm.

---

### Post by FAILINX on 2008-01-30
Thanks bud last glitch I needed to take care of!

---

