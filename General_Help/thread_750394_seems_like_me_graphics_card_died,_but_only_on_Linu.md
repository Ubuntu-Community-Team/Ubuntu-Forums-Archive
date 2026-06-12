---
title: "seems like me graphics card died, but only on Linux..."
date: 2008-04-09
forum: General Help
---

### Post by fargoth on 2008-04-09
Hello, I have been using Ubuntu on this computer for more then a year, and it worked perfectly.
Last week, i came home and found my computer in bad shape - the windows weren't drawn right, and videos only play on parts of their canvas - and only on odd lines (as you can see in the screenshot I've added).
my computer haven't been updated or anything before this happened, but just in case something went wrong with my graphics driver, I've upgraded my system to 8.04 beta (which has a new kernel and a new restricted driver module with a different version of nvidia's driver).
It still doesn't work right...
So I assumed my graphic card just died... after all, it's more then 5 years old GeForce 4200ti, and it's fan stopped working about a year ago...

but then, just for curiosity's sake, i booted into my old windows XP, and amazingly it works alright!
So, it's not a hardware problem, as far as i can tell, but i don't know what went wrong with my Ubuntu... so, any ideas?

[my screenshot]("http://img368.imageshack.us/my.php?image=screenshot1mk9.png")

update:
when viewing movies in full screen mode it plays great, but in a window it acts wierd...

---

### Post by xarquid on 2008-04-09
Looks like your video card is over heated -OR- your video driver is your completely off in Linux.

However, if your video card is over heated...it would still be creating graphic anomalies in Windows, I would think.

What graphics card are you using exactly? Are you using a restricted driver? When did the problems start occurring? Did you make any changes? Did anything install? Do you leave your P.C. running 24/7?

Thanks for your answers in advance. They will help us answer and assist.

xq

---

### Post by danwood76 on 2008-04-09
> **fargoth said:**
> 
but then, just for curiosity's sake, i booted into my old windows XP, and amazingly it works alright!
So, it's not a hardware problem, as far as i can tell, but i don't know what went wrong with my Ubuntu... so, any ideas?


It could still be an issue with your card, windows might not be driving it as hard as gutsy so its no real test.
And if you say the fan stopped working a year ago then I would say it is most probably borked.
The drivers are different from linux and windows so the hardware acceleration is different so its not a good test.

---

### Post by cdenley on 2008-04-09
What windows drivers are you using? If you don't install the nvidia drivers in windows, I think it usually uses the windows equivalent of the vesa driver. I don't think vesa uses the graphics cpu.

---

### Post by fargoth on 2008-04-09
> What graphics card are you using exactly? Are you using a restricted driver? When did the problems start occurring? Did you make any changes? Did anything install?

all this information is in my first post, but i'll repeat it for you:

1. my graphics card is GeForce 4200ti
2. I'm using the restricted drivers, and after the problem started i upgraded the drivers to a newer version (it didn't help)
3. the problem started last week, I made no new installations, and no upgrades...
> What windows drivers are you using? If you don't install the nvidia drivers in windows, I think it usually uses the windows equivalent of the vesa driver. I don't think vesa uses the graphics cpu.

I'm using nvidia's drivers on windows, vesa sucks.

I should try running a game on windows and see what happens...

It's still odd that i can watch a movie on Ubuntu in full screen mode, but when i switch to windowed mode, it freezes the image... 
anyway, I'll be back after the game test...

---

### Post by danwood76 on 2008-04-09
its to do with the graphics layer being used.
When you have it windowed you have other stuff using the rendering engine, like gnome, compiz etc.

When in full screen just the video is going through the rendering engine so it should render better.

---

### Post by fargoth on 2008-04-09
Well, I guess it's the hardware after all - started farcry, and it has lots of artifacts... 
So, next week I'll have a new graphics card...

---

