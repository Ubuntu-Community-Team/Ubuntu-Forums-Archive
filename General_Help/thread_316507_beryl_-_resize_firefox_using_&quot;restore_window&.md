---
title: "beryl - resize firefox using &quot;restore window&quot; makes firefox change to a small size"
date: 2006-12-10
forum: General Help
---

### Post by anasazi on 2006-12-10
When a Firefox window is maximized and I click the "Restore Window" button the window resizes to about 150px x 200px. I can resize the window just fine, but its a pain in the butt to have to drag every Firefox window to make them bigger.

When I change the size of a particular Firefox window it will then always "restore" into that same size, not the small size. However, new Firefox windows will then still size down into the small size.

No other programs that I can tell have this issue, just Firefox.

Did I miss a setting somewhere? I've searched and didn't find anything related to this issue, which appears to be my last major Beryl issue.

---

### Post by smallie on 2006-12-20
> **anasazi said:**
> When a Firefox window is maximized and I click.....

I have precisely the same problem under openSUSE 10.2  with nvidia driver..

---

### Post by xabbott on 2006-12-21
Same here... must just be a Beryl bug.

---

### Post by Astro96 on 2006-12-21
Yep, me too.  What a pain.  Anybody have a workaround?

---

### Post by DarkN00b on 2006-12-22
This is going to sound obvious, but this took me a while to figure out. :confused:  ](*,) 

1.  Maximise your window.
2.  Restore your window to the small size.
3.  Resize the window to the desired size by dragging the window edges.
4.  Maximise the window again.

It should now "restore" the reset size. If you can't resize the small window, open Beryl Settings and make sure Resize Window (in the left pane) is checked. You should then be able to resize the window.

---

### Post by Astro96 on 2006-12-22
But that doesn't save the settings after the applications is closed, does it?

---

### Post by DarkN00b on 2006-12-22
I don't know. All I'm sure of is that the "small window" thing happens occasionally and this is how I fix it. The correct window size does persist (most of the time) between browser sessions, even through system restarts. This was originally caused on my system by my dragging a maximised window down until it snapped loose from the top of the screen. I have to fix this a couple of times a week because I forget not to do that. :redface:

This problem mostly went away after I started using Beryl 0.1.3.

---

### Post by Astro96 on 2006-12-22
Your post made me check my version -- I was running 0.1.1.  Upgraded to 0.1.3 but I'm still having the same problems.

That fix didn't seem to work in 0.1.3 either.

Andy

---

### Post by DarkN00b on 2006-12-22
Well that's odd. I'm sorry I couldn't help more, but that's all I know to try.

---

### Post by l.tambiah on 2007-01-06
I am running 0.14 beryl and have that same issue with firefox on my laptop and desktop. I don't seem to be able to find away to get around this issue.

---

### Post by Choad on 2007-01-06
same here. using nvidia drivers with a geforce go 7600

i also get it that sometimes when maximising, the window's origin is set a few inches in from the top left, instead of being in the propper top left where it should be when maximised. a single click fixes this, but its annoying. 

additionally, sometimes a window will dissapear completely when maximising, and the only way to get it mack is to close it and open it again. good job ctrl+s brings up a seperate window else i would be much more angry at beryl ;)

edit: also, i find it wierd that some things in beryl are so slow. the MOST useful feature, scale, is very stuttery. yet it shouldnt really be doing any more work than anything else. the alt-tab switcher works very smooth. the cube is great. 

also simply dragging windows creates stutter. its wierd coz i can be playing planeshift at the same time, get no lag in planeshift, and still no difference in beryl,it still lags just the same, no more, so its not my gpu being under too much strain. how wierd.

---

### Post by l.tambiah on 2007-01-06
This bug could *possibly* be related to the *combination* of **XGL** and **Beryl**. Actually I have found my laptop is working okay with firefox now but is using **AIGLX** and **Beryl**. 

My Desktop uses **NVIDIA** and therefore I have went with **XGL** (as you need to use beta nvidia drivers for **AIGLX**). I removed my current Beryl installation and used compiz instead, and compiz doesn't suffer from the firefox issue on the clicking of the minimise button.

---

### Post by klep on 2007-01-07
hello all, 

I've got the exact same issue. was using 0.11 and when i Restore Window on firefox it goes to a ridiculously small size in the top left. Even more annoyingly the title bar is off screen so i cant even move it easily.

I upgraded to 0.13 ages ago and the problem persisted. Finally I have just upgraded to 0.15 and the problem is still there. It's really very very annoying.


I've noticed though that there is a problem with a lot of window sizings. For example, when I open a folder on my desktop it appears to be fullscreen but it actually isnt maximised - it is just stretched to take up the width of the screen. This is bizarre and somwhat annoying too (its not remembering how I sized the window because i would just maximise rather than stretch the window to that size).


I've checked the beryl forums but only ever spotted the odd person complaining about window sizing and no one really replies.

I'm on edgy using beta nvidia drivers

---

### Post by Armaniboy on 2007-08-08
I'm having the same issue as well. :KS

---

