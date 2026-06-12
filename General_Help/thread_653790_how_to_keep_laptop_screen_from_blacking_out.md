---
title: "how to keep laptop screen from blacking out?"
date: 2007-12-30
forum: General Help
---

### Post by Preserved_Killick on 2007-12-30
Running Gutsy on a Dell 700m. 

When watching movies, the screen goes black every 15 minutes (or so) and I need to bring it back by touching a key or the touchpad. I have "sleep" set to never in both ac and battery  to no use. Any suggestions? I see that I can uncheck power management in my Services, would that help? What does "power management" do? I have two power managements ACPID and APMD. 
Thanks for any advice you may have.

_jeff

---

### Post by 0g_Trans_Fat on 2007-12-30
If you go to System>Preferences>Power Management

There are tabs 'On AC power' and 'On Battery Power', under the display, it says: "Put display to sleep after inactive for:" then a bar, that you can adjust the time.  This is the time before it will dim the display to black.  You can set this to 'never' by moving the bar all the way to the right.

---

### Post by Hmarroqu on 2007-12-30
Have you checked the Screen Saver

---

### Post by Enginirical on 2007-12-31
I had the same (unresolved) problem in feisty and now the same issue in Gutsy. All the power management settings are set to never and I have not selected screen saver either!

The problem is deeper than just power management or screen saver settings, but have no clue what it could be!? Is there some kind of hidden default setting for laptops? or could it be BIOS related? no idea :(

*EDIT*

I found this, here: [http://ubuntuforums.org/archive/index.php/t-442190.html](http://ubuntuforums.org/archive/index.php/t-442190.html)

Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

I tried it, and all I can say so far is that the graphics card still works. I will leave my laptop running tomorrow to see if it has cured the problem then let you guys know!

UPDATE: ok, well it seems to have resolved the screen blanking problem, however there are other weird things going on: I found in another post that this solution would mean you could not use the screensaver. Well the screensaver works still since I selected 1min idle to test it. But when I went back to uncheck or change the idle time, when clicking screensaver in system preferences it would suddenly log me out of the current session! The only way to stop it is to really quickly click on the screensaver window which seems to prevent ubuntu from logging me out of the current session. To be honest although not ideal, It´s a fair swap and I rather my screen stops blacking out.

---

