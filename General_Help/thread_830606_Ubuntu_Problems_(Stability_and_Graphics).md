---
title: "Ubuntu Problems (Stability and Graphics)"
date: 2008-06-16
forum: General Help
---

### Post by Lemons on 2008-06-16
Let me just say that I know way intend to leave ubuntu, because I like this operating for several reasons:

Im on Hardy with a nVidia card.

1) Its user friendly.
2) Installing several new apps is a breeze (Even if a .deb is required)
3) WINE removes my need for windows (Flash 8+Screamer Radio)
4) Nice graphics

Now, 2 problems are getting in my way. These are probably due to my tinkering with the files. But here are the problems I am having, and any help would be greatly appreciated.

#1) When loading, the loading bar gets to the top, skips back a third of the way, loads again, and then shows segmentation errors (I know thats vague, I can look into any files if needed, such as logs).

#2) When loaded (If it does), login only works a rough 25-30% of the time. Else it locks up (Can move mouse, shutdown/restart thats it) at the screen.

#3) My screensaver never loads, and I get an error along the lines that the screensaver server/application is not running.

#4) If I leave my computer unattended, it will eventually freeze.

#5) A wine problem (No need to be answered), but due to the problems with the linux version of Skype, I run 2.5.x on WINE. ALSA Recording is great (Compared to OSS using padsp) but I cant hear a thing. Any help is thanked.

Those are my current problems with Ubuntu. The second one (Which is most likely caused by the first one) is my biggest headache. #3/#4 are a big deal because of #1/#2. #5 is just if anyone knows this.

Well, thanks anyone for any help!
~Kris

---

### Post by SteveNorman on 2008-06-16
what happens if you type in this:

```
glxgears
```

at the command prompt?

---

### Post by Lemons on 2008-06-16
Theres some gears spinning (Shows 3D acceleration, correct?). The driver does work, but after installing those instabilities (#1/#2 on my list) happen. And the screensaver such.

---

### Post by SteveNorman on 2008-06-16
how much ram do you have? sounds like a memory issue if your video drivers are good

---

### Post by Lemons on 2008-06-16
Well, if it would be a big problem, thats probably it. I have 3 sticks or ram, totalling 1GB. So no DDR, only a gig, and the video card has 128mb. Im also running compiz + AWN.

---

### Post by bingoUV on 2008-06-16
wait for 15-20 seconds after starting glxgears. It will print frames per second that your screen is geting from graphics card. Post it here so that someone can figure out if your graphics driver is working fine or not. Also post which nvidia graphics card you have.

---

### Post by SteveNorman on 2008-06-16
whats the output of

```
lspci | grep VGA
```

---

### Post by Lemons on 2008-06-17
The output is this:

02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

If this helps, I get traces when booting, or it says something about segv crashing, or a process. Any way I can get some logs to help home in on the problem?

Also, thanks for your help so far,
~Kris

---

### Post by SteveNorman on 2008-06-18
You may need a better vid card or at least the latest driver.
I would start here:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

the get nvidia-settings loaded

sudo apt-get nvidia-settings

and see if the helps. Thats about the limit of my knowledge, if memory and hard drive are working okay, and the temp of you processor is not getting to hot then it seems like a graphics card/driver issue. You may want to re-post in a different area of the forum and see if someone more qualified can help if my answer doesnt solve it. Good luck

---

