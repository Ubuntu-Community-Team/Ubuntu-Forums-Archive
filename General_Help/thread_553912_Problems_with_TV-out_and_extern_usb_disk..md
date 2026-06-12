---
title: "Problems with TV-out and extern usb disk."
date: 2007-09-18
forum: General Help
---

### Post by qweac on 2007-09-18
Hi!

I installed ubuntu a couple of days ago and this is the first time I try Linux. I have always used Windows.. I have two problems that really irritates me and they makes me think about going back to Vista. I have googled many hours in search for an answer, but nothing has worked, yet.

1. Tv-out won't work! I have nvidia 7600go, and I have installed the driver. The "nvtv tv out" program won't work at all. When I open it nothing happens. I have tried another program called "yanc", but that didn't work either. I only got a grey window with nothing in it. I have tried "sudo nvidia-settings", but I can't make it right in there either. The application can't save my settings to x. (or something like that.) I have also tried several guides on the internet where I edited the x file. I always end up with an error on boot and I have to restart the x file to continue. I have even tried some guides several times to make sure that I did everything right, but it won't work!

2. My WD external disk suddenly stopped working. I can't mount or unmount it. It works on my other computer with XP. I have reinstalled ubuntu and that worked, but it stopped working again earlier today. I have tried several things that I found when I googled, but...

I would really appreciate if anyone could help me with my two problems! I really love ubuntu, but these things really bothers me. Remember that I am a complete noob with the whole Linux consept so please explain things as good as you can!

Thanks! =)

---

### Post by qweac on 2007-09-18
I have a little update on the situation with the TV-out.

I now get picture on both screens in clone, but since my laptop is widescreen and my TV is not, I can't have it that way! I want to use "leftof" but it do not work! It works perfectly in the "login" screen, but once my password is entered correctly, and the desktop appears, the TV turns black. Why? This is a part of my X:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option "NoLogo" "1"
    Option "ConnectedMonitor" "crt, crt"
    Option "NoPowerConnectorCheck"
    Option "TwinView" "1"
    Option "Metamodes" "1280x768,800x600; 1024x640,800x600; 1280x768,NULL; 1024x640,NULL"
    Option "SecondMonitorHorizSync" "31-50"
    Option "SecondMonitorVertRefresh" "30-50"
    Option "TwinViewOrientation" "LeftOf"
EndSection

---

### Post by qweac on 2007-09-24
Bump

---

