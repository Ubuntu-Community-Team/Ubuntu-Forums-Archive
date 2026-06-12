---
title: "Normal mode hangs, only recovery mode starts up"
date: 2008-03-12
forum: General Help
---

### Post by arkroan on 2008-03-12
Dear Ubuntu friends,

I am having a problem starting my Ubuntu system in normal mode.. 

GRUB starts and system seems to start but I get a blank screen before the Log-in screen appears.

I have also noticed that during normal start-up, the lines:
 "Setting system Clock"
"Mounting root filesystem"
"Loading init-bottom" (or something like that)
"Loading hardware drivers"
 do not have an "OK" indication.

The recovery mode works fine.

The system was working fine until I booted up in windows and the computer crashed. In windows I have used the DiskInternals Linux Reader to retrieve a file, and then closed all applications to shut-down windows.

Please post any suggestions you might have on how to correct the problem.

I have a presentation on Friday with software I have been using in Ubuntu and I do not want any bad surprises. 
And It will not look nice if people see me booting in recovery mode.

My system is Ubuntu 7.10 Gutsy Gibbon in a Compaq R4000 AMD 64 Athlon.

---

### Post by ibuclaw on 2008-03-12
First, can you actually start X in recovery mode?

This can be tested by typing in:
```
 startx 
```

Though make sure that your internet connection is turned off first. As you'll be root and will have unlimited access to your entire system.

Or if you feel that you don't want to for risk reasons, starting ubuntu with Normal Startup, but switch to a virtual terminal (Alt + F1) will have the same desired effect.

Iain

---

### Post by arkroan on 2008-03-13
Hello tinivole,

Thank you for your reply.

I am sorry i was not more specific.

When i start my system in _normal mode _ it hangs right before the login screen. 

The first time it happened, i have tried to switch to a virtual terminal.. There was nothing displayed in the screen that indicated that i was in a terminal, but when I _blindly_ typed in :
 ```
shutdown -h now
``` 
the system shut down.

Now _I am not able_ to get a terminal at that point. I just have a blank screen and nothing else works. I have tried switching to a virtual terminal but nothing happened. I have tried to type in commands blindly (like ls -l /home/username/ and shutdown -h now) just to produce some hard disk activity, or switch off the system, but it does not work anymore.

On the other hand, recovery mode works like a charm.. But since I am a newbie and I can not afford damaging my system at this point (for reasons mentioned earlier) I would feel better working on normal mode.

---

