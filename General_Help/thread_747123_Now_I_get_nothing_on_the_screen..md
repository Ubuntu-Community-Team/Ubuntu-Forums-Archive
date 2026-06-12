---
title: "Now I get nothing on the screen."
date: 2008-04-06
forum: General Help
---

### Post by AquaStreak on 2008-04-06
(I'm on Windows XP to post this message)

First off, I have an ATI Radeon X1300 Pro graphics card. I know Ubuntu doesn't like those, so I was using restricted drivers.

Heres my story:

I was having a problem playing mp3 files, so my friend Joe told me to reboot (he said that should fix it).

When I rebooted, I was estatic that my sound was working (the drums and the logon sound), but was really confused when I was in 800x600 (on my nice 19" monitor). It told me I was in "low graphics mode" and 800x600 was the highest I could go).

I log into Pidgin, and my friend Joe asked me about my restricted driver setting. Turns out it was disabled (which honestly have been something I may have done previously without realizing it). So I check the box to reenable my drivers, and it requires a reboot.

So I press the icon it made to reboot on that top bar. I go to log into Ubuntu and...... nothing. No screen. Black. Void. Nothing.

My computer is running, I can tell by the fans. But I can't get ANYTHING to appear on the screen. So I turn off my PC by holding the power button down for like 10 seconds, and boot into Windows XP (I'm dual booting XP and Ubuntu).

Windows is working fine (which is how I can post this). I ask Joe what went wrong, and he had no idea. So, I think maybe it was just a fluke, and I try to log in again.

I still get nothing on the screen, but I realized I can log in. After I heard the drumroll, I typed "aquastreak" (my username), pressed enter, typed my password, pressed enter, and heard the welcome sound. I just see NOTHING on the screen.

So.. yeah. Please help. I'm having nothing but problems with Ubuntu and I regret ever trying it.

---

### Post by overdrank on 2008-04-06
> **AquaStreak said:**
> (I'm on Windows XP to post this message)

First off, I have an ATI Radeon X1300 Pro graphics card. I know Ubuntu doesn't like those, so I was using restricted drivers.

Heres my story:

I was having a problem playing mp3 files, so my friend Joe told me to reboot (he said that should fix it).

When I rebooted, I was estatic that my sound was working (the drums and the logon sound), but was really confused when I was in 800x600 (on my nice 19" monitor). It told me I was in "low graphics mode" and 800x600 was the highest I could go).

I log into Pidgin, and my friend Joe asked me about my restricted driver setting. Turns out it was disabled (which honestly have been something I may have done previously without realizing it). So I check the box to reenable my drivers, and it requires a reboot.

So I press the icon it made to reboot on that top bar. I go to log into Ubuntu and...... nothing. No screen. Black. Void. Nothing.

My computer is running, I can tell by the fans. But I can't get ANYTHING to appear on the screen. So I turn off my PC by holding the power button down for like 10 seconds, and boot into Windows XP (I'm dual booting XP and Ubuntu).

Windows is working fine (which is how I can post this). I ask Joe what went wrong, and he had no idea. So, I think maybe it was just a fluke, and I try to log in again.

I still get nothing on the screen, but I realized I can log in. After I heard the drumroll, I typed "aquastreak" (my username), pressed enter, typed my password, pressed enter, and heard the welcome sound. I just see NOTHING on the screen.

So.. yeah. Please help. I'm having nothing but problems with Ubuntu and I regret ever trying it.
Hi when you reach the login screen (or where you enter your user name before you here the drums) use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
```
I would also suggest Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 Hope this helps and good luck!

---

### Post by rafttrip on 2008-04-28
I am having a similar but more difficult problem. I have installed Ubuntu on my Sony laptop and I like it so I was looking forward to installing it on my desktop as well.

I insert the Live DVD of Gutsy i think 7.10 and reboot. I get the list of options "Install or Boot Ubuntu" so I hit enter and then I get the splash screen while it boots. then the screen goes blank and displays "No Signal" as in the cable is plugged in than I get the sound of the desktop coming on and still black screen. I have an ATI Radeion x1300 pro video card and apparently Ubuntu doesn't like this. I success fully booted Knoppix but I would prefer to run Ubuntu.....  My question is is this problem fixed in 8.04 or should I try something else since I can't do anything with 7.10 the way it is at the moment.

Any help would be appreciated.
Thanks:)

---

