---
title: "24: Lock screen never suspends monitors"
date: 2024-06-04
forum: General Help
---

### Post by AutoDMC on 2024-06-04
Hello!

I have an Apple Studio Display as my primary monitor*, and as such I don't have a power button available.  When it's time to go to bed, I like to lock my computer, as with MacOS and Windows this will allow the monitors to go to sleep pretty quickly (and if not, I press "escape" and the monitors sleep).  Then I unlock the next day and move forward, leaving my computer running all night to think deep thoughts.

On Ubuntu 24, however, when the screen blanks, it just draws black pixels across the monitors, but both monitors (the Studio and my Acer 1440p monitor) stay powered on all night.

I've tried setting the blank screen delay, which works on the desktop.  The screen fades after the time limit and then the monitors go to sleep.

However, the monitors never sleep on the lock screen.

Short of setting the screen blank delay to something tiny when going to sleep, or waiting for the 10 minute timer to tick by... how do I tell the lock screen to behave like the desktop and suspend the monitors?

(* I got the Studio Display when my daily driver was my MacBook.  I upgraded to a nice PC with Ubuntu, but still want to use my needlessly expensive monitor.)

---

### Post by currentshaft on 2024-06-04
The screens do not turn off because the system is only locked, not suspended.

Check the Power tab in Settings, you should be able to adjust it accordingly.

"systemctl suspend" is also a command you can use to suspend the system immediately.

---

### Post by AutoDMC on 2024-06-04
That is very true, yes!  However, I want the computer to stay operational;  I have stuff running overnights usually.  If there's nothing running overnight, might as well turn the computer off.  But this is a case where I might have some long running task going, and I want to keep the computer online and running, but I want to be able to have my monitors shut off because I'm on a lock screen.

Again, worst case I can switch the blanking time to something low and/or just wait 10 minutes for the monitors to blank, while leaving the computer unlocked.

Preference, though, is I can lock the computer, leave it running on whatever I'm doing, and have the monitors shut off.

I've done some research, but I don't know what state Ubuntu is in when it's locked;  I don't know if there's some other state that needs to be told it can blank.

---

### Post by currentshaft on 2024-06-04
I just tried "xdg-screensaver lock" on my Thinkpad laptop and it locked the screen and turned my screen (OLED) off. You're saying when you do this, external monitors remain backlit?

---

### Post by sebastjava on 2024-09-11
> **currentshaft said:**
> I just tried "xdg-screensaver lock" on my Thinkpad laptop and it locked the screen and turned my screen (OLED) off. You're saying when you do this, external monitors remain backlit?

Exactly. The screen is black, yes, but I can see it is still on, and backlit. That screen is simply displaying a black image...

But I think I found the fix for this. Short story, I found I just had to play with the "joystick" behind my screen: **Settings > Input > Auto Input Switch: Off** (So there is no auto-switching between HDMI and D-SUB.) That way the screen isn't just looking black, it is really off when you press Super+L or when you do "xdg-screensaver lock".

My complete story can be found on [https://www.facebook.com/groups/ubuntudistros/](https://www.facebook.com/groups/ubuntudistros/) Here's a copy-paste from that Facebook group:

[SIZE=4]Screen turns back on after being locked (SOLVED!)[/SIZE]

I press Super+L to lock the screen and make it go blank, i.e. turned off. Or I just wait 15 minutes for the screen to go blank, as set in Settings > Power. In both cases, the screen turns off for a few seconds, and then back on. The screen is black, yes, but I can see that it's not really off, it's just my LCD-LED screen displaying a black image while still being backlit.

That's not what I was expecting. The screen is wearing out, slowly but surely...

I am on Ubuntu 24.04.1 LTS, on a regular Wayland session, with a regular, new, mass-market IPS FHD LCD-LED screen: LG 24MR400-B.

I tested many things. I did a logout/login into Ubuntu on Xorg (X11). From there, I tried Super+L to lock the screen, again, and faced the same problem as on Wayland.

I also tried "sleep 3; xset dpms force off" from the terminal. The problem is more obvious this way: the screen comes back fully lit just a few seconds later, with the desktop and everything clearly visible. (No, I did not touch the mouse or the keyboard...)

NOW SOLVED ! I forgot to mention something... This problem started to appear after I changed my screen for a new one. I never had this problem before, on my old one. So, I tried changing a few things on the screen itself, that LG 24MR400-B...

BINGO ! I found I just had to play with the "joystick" behind my screen: **Settings > Input > Auto Input Switch: Off** (So there is no auto-switching between HDMI and D-SUB.)

Now I am back on my regular Wayland session, on Ubuntu 24.04.1. I have no problem at all. Screen lock, screen blank, computer suspend, name it, everything works fine.

I thought it was worth reporting this here, because I know other people are facing this problem too, on other brands/models, on Ubuntu and on other Linux distributions...

---

### Post by sebastjava on 2024-09-11
[B]Two questions:
[/B]
[LIST=1]
[*]I am pretty sure my story is pretty much the same as the OP. Was I right to post this related information here, or is that considered misconduct!? (I am new here, migrated from Linux Mint to Ubuntu on last June...)
[*]This problem seems to originate from the monitor itself, but that's not totally true. I don't have a deep knowledge and understanding, but I feel the HDMI cable is bi-directional, and the video card switches back on when it receives some signal from the monitor. Again, this problem only occurs when the monitor is set to auto-switch between HDMI and D-SUB. Anyway, I feel the computer should ignore any signal coming from the monitor, so the video card doesn't turn back on when it is time to go to sleep... Short story, I feel there is something that could be improved in the system. Some bug report to be made on Ubuntu. Where? Launchpad?
[/LIST]

---

### Post by inputpower on 2024-10-25
I have a dual monitor setup, two Dell monitors. I set one to not auto select and it did not resolve the issue. I then changed both Dell monitors to not auto select input, now it works. 

Thanks all!

---

