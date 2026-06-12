---
title: "BSOD !!! Black screen of death in Ubuntu 7.04"
date: 2007-07-09
forum: General Help
---

### Post by alperyilmaz on 2007-07-09
Hi I'm using Ubuntu 7.04 and I'm experiencing a problem with my system lately. When I leave the computer alone for a while, I find the system dead when I come back. The screen is black, probably turned off, wireless and power leds are on. The keyboard does not respond, even when i press caps lock its sign does not lid. Ctrl+Alt+Del or Ctrl+Alt+Bkscp does not help. If I find the system dead like that only thing I can do is turning off the machine by pressing and holding the power button. 

I am not sure if X is crashing or not. But I'm guessing that if it was X crashing, caps lock lid should work or ctrl+alt+F1-6 should work. I manually edited X.org file months ago to setup dual monitors. I couldn't have X generate dual monitor view despite long hours of search and X.org manupulation.

I don't remember when computer started acting like this, I'm not sure after installing what program computer acted weird. But I frequently install, check, uninstall softwares.

Before switching to Ubuntu, I remember reading somewhere that after suspend of hibernate some laptops crash. I don't know if this is the case for me. I have Dell Inspiron 700m. Do I need to edit some config files so that system does not crash after resuming from suspend or hibernate?

I tried to look thru system log files and tried to pinpoint what had happened just before the crash. I didn't see a particular software causing this or not (btw, I'm novice linux user, the phrase "I didn't see.." does not reflect an expert's idea)

I would greatly appreciate any help regarding the black screen of death :)

---

### Post by stchman on 2007-07-09
> **alperyilmaz said:**
> Hi I'm using Ubuntu 7.04 and I'm experiencing a problem with my system lately. When I leave the computer alone for a while, I find the system dead when I come back. The screen is black, probably turned off, wireless and power leds are on. The keyboard does not respond, even when i press caps lock its sign does not lid. Ctrl+Alt+Del or Ctrl+Alt+Bkscp does not help. If I find the system dead like that only thing I can do is turning off the machine by pressing and holding the power button. 

I am not sure if X is crashing or not. But I'm guessing that if it was X crashing, caps lock lid should work or ctrl+alt+F1-6 should work. I manually edited X.org file months ago to setup dual monitors. I couldn't have X generate dual monitor view despite long hours of search and X.org manupulation.

I don't remember when computer started acting like this, I'm not sure after installing what program computer acted weird. But I frequently install, check, uninstall softwares.

Before switching to Ubuntu, I remember reading somewhere that after suspend of hibernate some laptops crash. I don't know if this is the case for me. I have Dell Inspiron 700m. Do I need to edit some config files so that system does not crash after resuming from suspend or hibernate?

I tried to look thru system log files and tried to pinpoint what had happened just before the crash. I didn't see a particular software causing this or not (btw, I'm novice linux user, the phrase "I didn't see.." does not reflect an expert's idea)

I would greatly appreciate any help regarding the black screen of death :)

Turn off suspend and hibernate.  They don't work that well in Feisty.

System--->Preferences--->Power Management

---

### Post by AlexThomson_NZ on 2007-07-09
Is your PC set to sleep after a certain amount of time?  Does this happen when this is disabled?

// Beaten by stchman

---

### Post by alperyilmaz on 2007-07-09
the computer was set to sleep after 30 mins (on battery) or 1 hour (on AC). But blank screen of death does not happen after 30 mins or 1 hour. It's way shorter than that. For instance, yesterday it happened after 15 mins of inactivity. Right now I removed "suspend and hibernate after certain amount of activity" feature. Let's see if it helps..

---

### Post by Xizorbg on 2007-08-29
Hey All-

My computer running Feisty will not boot now after being powered down!  Any ideas for fixing it.  Tried running rescue system from Alternate install CD.  I am running Feisty 7.04 on AMD 64bit system, ASUS A8V MB with ACPI enabled and S3 mode enabled.  Tried disabling and booting again, but only got BSOD after kernel boots....

Any ideas?  Troubleshooting?

I would rather not reinstall Feisty (again).

Thanks,
X

---

### Post by kaurman on 2007-12-31
> **alperyilmaz said:**
> Hi I'm using Ubuntu 7.04 and I'm experiencing a problem with my system lately. When I leave the computer alone for a while, I find the system dead when I come back. The screen is black, probably turned off, wireless and power leds are on. The keyboard does not respond, even when i press caps lock its sign does not lid. Ctrl+Alt+Del or Ctrl+Alt+Bkscp does not help. If I find the system dead like that only thing I can do is turning off the machine by pressing and holding the power button. 

I am not sure if X is crashing or not. But I'm guessing that if it was X crashing, caps lock lid should work or ctrl+alt+F1-6 should work. I manually edited X.org file months ago to setup dual monitors. I couldn't have X generate dual monitor view despite long hours of search and X.org manupulation.

I don't remember when computer started acting like this, I'm not sure after installing what program computer acted weird. But I frequently install, check, uninstall softwares.

Before switching to Ubuntu, I remember reading somewhere that after suspend of hibernate some laptops crash. I don't know if this is the case for me. I have Dell Inspiron 700m. Do I need to edit some config files so that system does not crash after resuming from suspend or hibernate?

I tried to look thru system log files and tried to pinpoint what had happened just before the crash. I didn't see a particular software causing this or not (btw, I'm novice linux user, the phrase "I didn't see.." does not reflect an expert's idea)

I would greatly appreciate any help regarding the black screen of death :)

Hi!

I have exactly the same problem. I am using two monitors as well (a laptop and an external). The only solution I can offer for now is to turn off the "turn off monitor" setting in gnome power manager. Someone should probably fill in a bug report about that issue...

Edit: I'm using 7.10. And alperyilmaz, I think you should be the one who gets the honour of filling the bug report :) as you have described the problem well.

---

