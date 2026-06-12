---
title: "Need help in changing &amp; saving screen resolution in Ubuntu 14.04"
date: 2015-08-03
forum: General Help
---

### Post by adi9 on 2015-08-03
Hello, guys! [COLOR=#111111][FONT=Ubuntu]I have Ubuntu 14.04 with integrated Intel graphics card and AMD Raden R9 M275 graphics card. I have also installed AMD Catalyst Center to switch between Intel and Radeon. I followed this answer: [/FONT][/COLOR][How set my monitor resolution?]("http://askubuntu.com/questions/189246/how-set-my-monitor-resolution/189364#189364")[COLOR=#111111][FONT=Ubuntu] to set the resolution to 1600x900 (which was not in the original list of the resolutions).

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I am able to set the resolution everytime, but after every reboot or while playing a game (DOTA 2, here), the screen flickers and it goes back to the highest 1920x1080, along with a very tall error dialog box (a screenshot of which is attached). [/FONT][/COLOR][ATTACH=CONFIG]263593[/ATTACH][COLOR=#111111][FONT=Ubuntu]


[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I shall be really grateful if somebody could help me in setting the 1600x900 resolution permanently. Thanks![/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-08-03
Hi and welcome.

Are you using VGA? If so, don't. For your hardware use digital connections only (HDMI, DVI, DisplayPort, ...).

---

### Post by adi9 on 2015-08-03
> **Vladlenin5000 said:**
> Hi and welcome.

Are you using VGA? If so, don't. For your hardware use digital connections only (HDMI, DVI, DisplayPort, ...).

Hi, thanks for you reply. I can't say for sure about the VGA thing. I did this (from the askubuntu forum question:

```
[COLOR=#111111][FONT=Consolas]xrandr --query | grep connected[/FONT][/COLOR]
```

and got this:

```
eDP1 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm

HDMI1 disconnected (normal left inverted right x axis y axis)
```

I guess it says and means it is connected to eDP1? Is this VGA? Can you please explain what to do now? I admit I am new to Ubuntu and learning daily.  :)

---

### Post by Vladlenin5000 on 2015-08-03
Physical connections/connectors between devices has nothing to do with operating systems. Irrespective of the OS you're running you should know how you're connecting the PC to the monitor.
If you aren't familiar with terms such as HDMI, DVI, etc. then maybe you should do some homework before using computers. Wikipedia is a good place to start.

By "VGA" I mean the old analogue [D-Sub]("https://en.wikipedia.org/wiki/D-subminiature") connector. Your xrandr results, however, suggest you're using [DisplayPort]("https://en.wikipedia.org/wiki/DisplayPort"). If so, I really don't understand why it isn't detecting the correct maximum resolution. Please post brand/model of the monitor. There's more: It should have worked _without_ the workaround you posted that, by the way, is for old monitors only.

---

### Post by adi9 on 2015-08-03
> **Vladlenin5000 said:**
> Physical connections/connectors between devices has nothing to do with operating systems. Irrespective of the OS you're running you should know how you're connecting the PC to the monitor.
If you aren't familiar with terms such as HDMI, DVI, etc. then maybe you should do some homework before using computers. Wikipedia is a good place to start.

By "VGA" I mean the old analogue [D-Sub]("https://en.wikipedia.org/wiki/D-subminiature") connector. Your xrandr results, however, suggest you're using [DisplayPort]("https://en.wikipedia.org/wiki/DisplayPort"). If so, I really don't understand why it isn't detecting the correct maximum resolution. Please post brand/model of the monitor. There's more: It should have worked _without_ the workaround you posted that, by the way, is for old monitors only.

I am really sorry, I should have mentioned that I have a laptop, not a desktop computer. It is Lenovo Y40-80. Also, it IS detecting the maximum resolution (the resolution to which the laptop reverts back to always), however, I want a mid-way resolution (1600x900), because the lesser resolution in 16:9 ratio is 1360x768, which looks really bad on this laptop. Hope I have cleared the situation further.

---

### Post by newcfd on 2015-08-03
take a look at here
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
you may be able to find a solution. Good luck!

---

### Post by Vladlenin5000 on 2015-08-03
Well, a laptop explains a lot indeed.

The link in previous post is quite "technical" but elucidative. It's definitely something worth knowing and yes, you can do those experiments. I mean, do exactly that, experiments. 
However, the general rule is and always has been the maximum resolution is THE resolution. There's no reason to use any other, period.

If your monitor is FullHD (1080P) and your graphics system handles it fine (it's a machine designed to work like that so no surprise here) why use another? Really, why? I can't think of a single (rational) reason for trying to lower it...

---

### Post by adi9 on 2015-08-03
> **Vladlenin5000 said:**
> Well, a laptop explains a lot indeed.

The link in previous post is quite "technical" but elucidative. It's definitely something worth knowing and yes, you can do those experiments. I mean, do exactly that, experiments. 
However, the general rule is and always has been the maximum resolution is THE resolution. There's no reason to use any other, period.

If your monitor is FullHD (1080P) and your graphics system handles it fine (it's a machine designed to work like that so no surprise here) why use another? Really, why? I can't think of a single (rational) reason for trying to lower it...

I want to use the mid-way one because the highest one makes everything too small to read. Eg., the font becomes smaller, icons become smaller, etc. Another way to put it would be the screen becomes zoomed-out way too much. In case of 1360x768 one, everything becomes big, i.e., zoomed-in.

However, the mid-way one (1600x900) looks and feels perfect for me, the perfect combo of small and readable. And I reiterate: I AM able to set this resolution (through the steps mentioned in the linked askubuntu thread), but the resolution reverts back to the highest one, with that large error dialog box (screenshot attached in the first post). Hope I made it clear.

---

### Post by Portaro on 2015-08-03
You can add a resolution optino to your autostart take a look here ->

[http://crunchbang.org/forums/viewtopic.php?id=27153](http://crunchbang.org/forums/viewtopic.php?id=27153)

xrandr --output default --mode **1360x768** --pos 0x0 --rotate normal

change the **1360x768 **to your desired resolutionand put a file on ~./autostartORTake a look here -> [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent](http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent)

> xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
  then I call it in /etc/lightdm/lightdm.conf
  display-setup-script=/usr/bin/lightdmxrandr


---

### Post by adi9 on 2015-08-03
> **newcfd said:**
> take a look at here
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
you may be able to find a solution. Good luck!

Thanks for the link. I went to the section of the method by which I changed the resolution, and it says this:

> [COLOR=#333333][FONT=Ubuntu Beta]in some cases panel windows may resize improperly as a result.[/FONT][/COLOR]

But it doesn't give any troubleshooting or any process on how to resolve this issue, sadly.

@Portaro

Thanks. Will look into the threads you posted.

I am still stuck, guys. Shall be grateful of any help. Thanks.

---

### Post by Vladlenin5000 on 2015-08-04
I'll be blunt as usual: You are and you'll be.
I don't support dirty, unprofessional "solutions". What I told you before is what should be. The only good resolution is the native one. Things get smaller? Well, sure... The whole point of higher resolutions is having smaller pixels.
You can then adjust the desktop settings to better fit what you're used to: Bigger icons, bigger launcher, bigger system fonts, etc. Everything available in the standard system settings and/or Unity Tweak tool (installable).

---

### Post by adi9 on 2015-08-06
> **Vladlenin5000 said:**
> I'll be blunt as usual: You are and you'll be.
I don't support dirty, unprofessional "solutions". What I told you before is what should be. The only good resolution is the native one. Things get smaller? Well, sure... The whole point of higher resolutions is having smaller pixels.
You can then adjust the desktop settings to better fit what you're used to: Bigger icons, bigger launcher, bigger system fonts, etc. Everything available in the standard system settings and/or Unity Tweak tool (installable).


Thanks. I will check out that tool. I didn't get this part though: "I'll be blunt as usual: You are and you'll be."

---

### Post by Vladlenin5000 on 2015-08-06
> I am still stuck

^^^^
This is what I should have quoted. Then the *You are and you'll be*[stuck] would have made sense. Sorry for not being clear in my rant ;-)

---

