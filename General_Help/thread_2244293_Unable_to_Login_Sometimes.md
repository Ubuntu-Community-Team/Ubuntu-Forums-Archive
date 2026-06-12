---
title: "Unable to Login Sometimes"
date: 2014-09-15
forum: General Help
---

### Post by eldavar on 2014-09-15
Good morning. I'm running Ubuntu 14.04 LTS. The problem is that sometimes I'm unable to login after the system resumes from sleeping. It doesn't happen every time, maybe 1 out of 3 or 4 times, which is enough to be very inconvenient. 

It seems to happen regardless of whether the computer actually went into sleep mode (where the monitors turn off), or just when the screensaver becomes active after a few minutes of inactivity. Also, it happens regardless of whether or not I manually locked the screen. 

In those situations, instead of being presented with the normal login screen, I'm presented with one that's slightly different. Let me explain...

I'm running 3 identical monitors, and my desktop wallpaper stretches across all 3. 

Here's the wallpaper: (click for larger size)
[[IMG]http://goo.gl/ey1zKi[/IMG]]("http://goo.gl/WdB7KL")

Here is what my normal login screen looks like: (click for larger size)
[[IMG]http://goo.gl/W5Ztiu[/IMG]]("http://goo.gl/9qqOjl")

You can see that the login screen is the middle third of the wallpaper (the center monitor). However, when this login problem occurs, the screen displays what looks like the left 2/3 of the wallpaper, shrunk to fit on one monitor. 

Here is the screen where I can't login: (click for larger size)
[[IMG]http://goo.gl/0pDNQK[/IMG]]("http://goo.gl/kZRIOU")

The box area where I should be able to type my password is non-responsive. There is no password entry text box. Clicking the area does nothing. Also, the usual stuff at the top right of the screen is missing (clock, network icon, volume icon, etc.). Plus, the computer name (greg-ubuntu) is displayed in the upper left corner. Clicking it does nothing. 

When this happens, I can't find a way to get back into my session. I can use CTL+ALT+F1 to login to a new session, and startx seems to work fine, but this does not get me back to what was on the screen before. 

Also, when switching to the tty1, the system displays some processes as it starts, and all show OK except for "SMB/CIFS File and Active Directory Server". This one says "fail" in red letters. (click for larger size)
[[IMG]http://goo.gl/4kba2q[/IMG]]("http://goo.gl/NDNm2s")

Is this related to the problem here? I don't know what SMB/CIFS actually is... 

I don't know what to do about this, and I don't know where to find logs that could provide relevant info about what's going on. Honestly, even if I found some logs, I wouldn't know what to look for anyway. This problem causes me to lose work sometimes, and it occurs randomly (of course, usually at the absolute worst inconvenient time). Any help would be greatly appreciated!

---

### Post by fyfe54 on 2014-09-15
I have this too.  

As a workaround, I click on my name in top right corner to get dropdown and a second time to close it.  Then clicking in the the password field works again.  

I did see a mention of it somewhere in the forums, but cannot remember where.  Sorry.

---

### Post by eldavar on 2014-09-16
My computer name appears in the top left when this problem happens, but clicking it has no response. Nothing at all responds no matter where I click. Right-click doesn't do anything either.

---

