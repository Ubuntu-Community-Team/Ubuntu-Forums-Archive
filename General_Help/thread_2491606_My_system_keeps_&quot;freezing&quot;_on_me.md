---
title: "My system keeps &quot;freezing&quot; on me"
date: 2023-10-14
forum: General Help
---

### Post by johnnybegood2222 on 2023-10-14
Today already, in the past hour, my system has froze on me.  What happens is that I can't click on anything to get it to open.  I can move the mouse over something and click - nothing happens.

I did a clean re-install of Ubuntu 22.x lts less than a month ago.  I don't know what's going on.  My only way to escape it is to do a shift+print screen+reisub

Any ideas what's happening ?  I've used Ubuntu for years and haven't had this problem before.

Addendum:  [COLOR=#000000][FONT=Verdana]It's an old one - an HP with a Core i5 vPro processor. I put new ram in it about a year or 2 ago - bringing it to 16 gigs ram. I also put a new SSD in it - a 1 terabyte one.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I guess it's time to replaced it. I can use my HP laptop until I replace it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Are there any apps/programs to test the hardware?[/FONT][/COLOR]

---

### Post by HermanAB on 2023-10-15
Howdy, 
In my experience - most of the time unreliable operation is caused by a bad PSU and bad capacitors on the mother board.  

The electrolytic capacitors are usually the first to go bad - that causes noisy power, leading to the processor making computational mistakes.

---

### Post by TheFu on 2023-10-15
I had an apparent lockup yesterday when I accidentally clicked on a movable firefox widget and dropped it somewhere else inside the same firefox window.  Fortunately, I have another computer and was able to ssh into the one with the lockup to see what was running.  Everything else on the computer, except the GUI was working, so I killed firefox.  Then I moved back to the first computer and saw that everything was actually fine.  Didn't even reboot. See:
```
$ uptime
 12:29:15 up 3 days,  4:34,  5 users
```

The point is that not all lockups are really system-wide. Sometimes 1 poorly behaved application can scew the GUI.  Figuring out which application that is usually isn't hard.  

In my situation, the system is this:
```
$ inxi -G
Graphics:  Device-1: AMD driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.13 driver: amdgpu,ati 
           unloaded: fbdev,modesetting,vesa resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-86-generic LLVM 12.0.0) 
           v: 4.6 Mesa 21.2.6 
```
So, a 20.04 computer using an amdgpu video driver and X11 (not Wayland). The version of Firefox was an ESR version running inside a firejail, but not a private firejail, so protections weren't all THAT high.  If it happens again any time soon, I'll worry more about it. I think is was a 1-off firefox issue.

Had I not recognized FF as the problem, I'd have looked in the system logs to see what errors and warnings were there around the time of the problem.  You can google how to see different system logs on Ubuntu. They are very helpful, if you don't let your eyes gloss over at all the details.  Just like when we all learned to read, we had to slow down, take 1 word at a time and slowly read through.  Logs are the same. Get passed the "too much" idea and just look for the things on lines with errors or warnings.

---

