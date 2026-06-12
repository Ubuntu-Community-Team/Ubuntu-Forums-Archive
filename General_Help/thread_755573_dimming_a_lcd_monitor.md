---
title: "dimming a lcd monitor"
date: 2008-04-15
forum: General Help
---

### Post by angryhomer17 on 2008-04-15
My monitor is often too bright for my tastes, especially in the morning when I just have woken up. I am looking for a way to dim it, or more specifically, to reduce the backlight below the firmware settings.

Here is what I have:
Acer AL2051W
Nvidia GeForce 7600GT
Xubuntu 7.10

Here's what I've already tried:
1. I can reduce the brightness/contrast using Nvidia X server color correction. This works as a quick fix, but it messes up the colors pretty bad. It's not something I would want to look at for an extended period of time.

2. Reduce the brightness on the monitor itself. It's set to 0 right now, but it's still pretty bright.

3. gddccontrol 0.4.2 It runs but I get an error: The current monitor is in the database but does not support DDC/CI. I have no idea what DDC/CI is. The current monitor is shows is a pci:01:00.0-1: VESA standard monitor

4. xvattr Doesn't appear to show any brightness settings.

So I'd like to reduce the backlight/brightness while still keeping colors vibrant. Thanks

---

### Post by Gen2ly on 2008-04-15
I wrote how to manually adjust brightness here, that might be worth a shot.

[http://ubuntuforums.org/showthread.php?t=755052](http://ubuntuforums.org/showthread.php?t=755052)

---

### Post by bingoUV on 2008-04-15
Some points :
1. Do you use compiz / desktop effects? It has a setting to see negative of the screen i.e. dark colors swapped with light colors. You can toggle it with <Super>+m
 .2. If you spend a lot of time at firefox / terminal / open office etc. they can be set to show a black background and white foreground( actually I prefer wheat color) You could try some xfce theme that is dark background if you mostly use xfce applications(Thunar etc.)

These points have nothing to do with monitor, but they do reduce the overall brightness of the screen.

---

### Post by angryhomer17 on 2008-04-15
@Dirk.R.Gently- Looked at the post and it appears that it is for laptops. I looked in /proc/acpi/video and didn't find anything. But that might be helpful for my laptop; I just dont use it a whole lot.

@bingoUV- No I dont use compiz/beryl. I've tried it before a few times and really didn't like the interface or its resource-intensiveness. Plus it's pretty much eye candy. Perhaps I will try it again when I upgrade to Hardy. 

I have tried changing the themes around a bit, and some seem to be ok, but I can't find a good way to tweak them. My terminal is white on black with some transparency, but I cant stand to read white text on black in a browser. I dont like thunar either; I use krusader.

And here lies the problem, customizing one part of the system may not customize it for all other parts. And sometimes that is good, but I wish there were an easier way to make system wide customizations that affect all apps. I guess I'll have to do some more reading.

---

### Post by bingoUV on 2008-04-15
I just proved to you that compiz is not just eye candy (negative, remember?) :) 
It has other benefits like zoom in on a particular part of the screen, transparent window (see whether you compilation has finished while browsing ubuntuforums without switching windows) etc. I agree that it is not for everyone.

krusader sounds like a KDE application. You might have to change your KDE theme, and then load KDE theme engine when your xfce desktop starts. Don't know much about KDE, but it might help you in searching.

---

