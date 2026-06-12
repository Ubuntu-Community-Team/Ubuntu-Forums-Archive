---
title: "Anti Aliased help"
date: 2008-01-08
forum: General Help
---

### Post by alejo0823 on 2008-01-08
Hi I have been trying for a while now to anti alias my screen but failed miserably, apparently its done with the nvidia configuration, I do that, set my anti aliased and I think it needs to reboot to aply the changes only it doesn't, its still all jagged. I'm thinkin its because its not using the nvidia configuration as the default configuration can any1 help me with this??

---

### Post by MobiusNZ on 2008-01-08
What exactly are you trying to antialias? Your fonts? Have a look in your preferences under fonts and you should find sub-pixel hinting which should do the trick

---

### Post by alejo0823 on 2008-01-08
No, I mean my whole screen the fonts the cube, the effects, the wobbly windows, everything. cuz I have a good video card and it would be a waste not to use it, plus AA makes everything look good.

---

### Post by MobiusNZ on 2008-01-08
OK, when you start the nvidia config program do you use gksudo? ie
```
gksudo nvidia-config
```
Otherwise nvidia-config runs as you, and you can't write the necessary settings.
Also, you don't need to restart fully - you can just log out then choose from the login menu "Restart X Server" - or, if all your programs are closed you can just hit CTRL-ALT-BACKSPACE (this method is a bit brutal, but quick)

---

### Post by alejo0823 on 2008-01-08
2 weird things when I did the command gksudo nvidia-settings it gave an error about my theme something about cant find an icon or something like it. no problem took my theme off then gksudo nvidia-config did nothing so I did gksudo nvidia-settings but the same thing the bars were already in 16AA and after restart the x server no AA
BTW thanks for the help

---

### Post by MobiusNZ on 2008-01-08
Sorry yes i did mean gksudo nvidia-settings... I used to have a nVidia card but I upgraded to an ATI so I'm a little rusty on some of the things.

I do remember nvidia-settings being a little bit funky sometimes. Try resetting to defaults, restarting X then trying again. Also, maybe try a lower AA - like 2 or 4.

---

### Post by alejo0823 on 2008-01-08
Ok tryed several settings still very jagged none worked I think nvidia settings only work for opengl aplications is the cube an opengl app?? how do AA directly from ubuntu is there a way??

---

### Post by MobiusNZ on 2008-01-08
Yeah I'm pretty sure that the compiz/fusion uses opengl. I think there might have been "force antialiasing" settings as well? Otherwise, yeah look for advanced properties for desktop effects. You might have to do a bit of searching in the forums (try the desktop effects section), as I'm actually using Kubuntu, which is hanging out for KDE4's effects and thus doesn't have compiz.

---

### Post by alejo0823 on 2008-01-08
Ok thanks for the help

---

### Post by alejo0823 on 2008-01-08
now I was able to solve the problem with help from this [http://ubuntuforums.org/showthread.php?t=646356&highlight=anti+aliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=anti+aliasing)

But the result gave me tearing in the windows due to bad sync and no Vsync can fix it so am back to 0 AA I'm not sure if I should put this post as solved cuz it was just partially solved so I'm still looking for help

---

