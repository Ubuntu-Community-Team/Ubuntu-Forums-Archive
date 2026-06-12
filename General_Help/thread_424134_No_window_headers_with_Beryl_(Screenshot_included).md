---
title: "No window headers with Beryl (Screenshot included)"
date: 2007-04-26
forum: General Help
---

### Post by flipjarg on 2007-04-26
i'm having a problem with Beryl in Feisty. i've installed Nvidia drivers and they seem to be working. i am able to rotate the cube and the windows get wobbly. The problem that i'm having is that there are no window headers on any windows, they aren't there at all. When i go back to Metacity (GNOME's default window manager) everything continues to work fine. 

Any ideas?

---

### Post by IronMan7491 on 2007-04-26
I can't recall exactly what it is called but if you go to the Beryl options and change the rendering option to something like  to copy rendering your borders will appear.

---

### Post by Zuph on 2007-04-26
First, try changing the emerald theme with beryl-manager, and if that doesn't work, add this to your xorg.conf file (in /etc/X11/) under "screens": 

Option "AddARGBGLXVisuals" "True"

Then restart X.

---

### Post by flipjarg on 2007-04-26
Adding the line in my xorg.conf doesn't do it. But i will keep an eye out for that option when i get a chance to look through the options.

---

### Post by ThrobbingBrain66 on 2007-04-26
Also, make sure that you are using the Beryl Decorator (right-click the Beryl icon).  I've experienced the same behavior if the Compiz GTK decorator is being used instead.

---

### Post by flipjarg on 2007-04-26
> **ThrobbingBrain66 said:**
> Also, make sure that you are using the Beryl Decorator (right-click the Beryl icon).  I've experienced the same behavior if the Compiz GTK decorator is being used instead.

Dang, i used the three options i have in that menu. i've reloaded the Window Decorator each time also. i'm going to sit down and try to find the option that IronMan spoke about.

---

### Post by spankymasterc on 2007-04-26
add this under Device

```
       Option         "AddARGBGLXVisuals" "True"
	Option         "RenderAccel" "True"
	Option         "AllowGLXWithComposite" "True"
	Option         "backingstore" "True"
	Option         "TripleBuffer" "True"
```

and add under Screen Section

under the deafaultdepth 

```
    Option         "UseFBDev" "true"
    Option         "AddARGBGLXVisuals" "True"
```

then restart X
```

Ctrl + Alt + Backspace 
```

log back in...

if you have any problems just go to recovery mode and type 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by flipjarg on 2007-04-26
i've tried everything above so far. i keep getting this message in the command line. It's been happening the whole time i've been trying to get Beryl to work. ```
beryl: No GLXFBConfig for depth 32

```

---

### Post by NullHead on 2007-04-26
Are you using nvidia-glx?

---

### Post by flipjarg on 2007-04-26
> **NullHead said:**
> Are you using nvidia-glx?

Yes, using nvidia-glx

---

### Post by NullHead on 2007-04-26
> **flipjarg said:**
> Yes, using nvidia-glx

I would try installing the drivers from [Nvidia's website.]("http://www.nvidia.com/content/drivers/drivers.asp")

---

### Post by veelo on 2007-04-28
This worked for me:
Right-click on the Beryl diamond in the dock and choose "Advanced Beryl options"->"Rendering path"->"Copy".

---

### Post by flipjarg on 2007-04-28
That's one of the first things i tried, changing all of the options under "Advanced Beryl Options". It made it impossible for me to navigate anything. From what it looked like to me it made two copies of my screen side by side. i can't tell for sure because everything is so distorted and everything is black and green. 

Maybe i'll just go back to using KDE. i do like GNOME though, but Beryl had a lot of things that helped me when i was working on things. Beryl makes it much easier to have a bunch of windows open at once and quickly navigate them. i can't go without it now!

---

### Post by NullHead on 2007-04-28
> **flipjarg said:**
> That's one of the first things i tried, changing all of the options under "Advanced Beryl Options". It made it impossible for me to navigate anything. From what it looked like to me it made two copies of my screen side by side. i can't tell for sure because everything is so distorted and everything is black and green. 

Maybe i'll just go back to using KDE. i do like GNOME though, but Beryl had a lot of things that helped me when i was working on things. Beryl makes it much easier to have a bunch of windows open at once and quickly navigate them. i can't go without it now!

If you can't get beryl to work and you can't live with out 3d, then you should give compiz a try;)

---

### Post by smifffy on 2007-10-25
Hi All,

I'm pretty new to both Linux and Ubuntu so bear with me. 

I'm seeing the same issue with no headers appearing on my windows.:confused: 

I've tried all the things referenced here on these pages and have used the restricted drivers manager to make sure I'm using the latest nvidia drivers. (Is there a better way?).

I'm using a Dell laptop XPS M1210. 

If I use Metacity everything is fine. Compiz & Beryl lose the window headers. I very much like the way of switching around the windows and the features of Beryl so would really appreciate help to get this sorted.

Cheers.

---

### Post by NullHead on 2007-10-25
> **smifffy said:**
> Hi All,

I'm pretty new to both Linux and Ubuntu so bear with me. 

I'm seeing the same issue with no headers appearing on my windows.:confused: 

I've tried all the things referenced here on these pages and have used the restricted drivers manager to make sure I'm using the latest nvidia drivers. (Is there a better way?).

I'm using a Dell laptop XPS M1210. 

If I use Metacity everything is fine. Compiz & Beryl lose the window headers. I very much like the way of switching around the windows and the features of Beryl so would really appreciate help to get this sorted.

Cheers.

Well for starters you shouldn't dig up old threads.

Did you install emerald? Compiz fusion has a configuration manager similar beryl's.

---

### Post by #Reistlehr- on 2007-10-25
try:

sudo nvidia-xconfig --add-argb-glx-visuals

And set the depth to 24 in the /etc/X11/xorg.conf file near the end

---

