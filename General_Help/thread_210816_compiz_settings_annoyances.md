---
title: "compiz settings annoyances"
date: 2006-07-07
forum: General Help
---

### Post by hotani on 2006-07-07
1- New development this morning: I noticed that every time I hit "Alt" the current window would get minimized. If I keep doing it of course, eventually everything is minimized. 

2- there is a setting *somewhere* that will turn off the massive annoying bouncing effect when a window is brought to the front, this is different on every machine and I have no idea where the setting is located, other than "somewhere in the wobbly settings."

3- transparancy of windows when moving just stopped today. No warning, just gone. It is still active in the control panel. 

4- alt-tabbing (my all-minimized windows) no longer spans the desktops, even though the setting is still checked.

5- many times the 'appearance' setting in the menu when right-clicking a title bar will be gone and I'll have to restart compiz to get it back.

A lot of this stuff just showed up today. Was there an update that caused it? Anyone else experiencing this weirdness? Compiz is cool and all but sometimes I end up spending way too much time getting just the right amount of effects with the least amount of irritation which is turning out to be a very difficult task.

EDIT: I uninstalled the 'vanilla' packages and installed the plain ol compiz + compiz-gnome which seems to have cured most of the problems. There are a couple of oddities still, but a lot of that is because I'm still trying to figure out these cryptic setting in the control panel.

---

### Post by hotani on 2006-07-07
Now I have GREEN shadows. The shadow color setting in gset-compiz is very clearly black, and yet mine are green. ideas?

---

### Post by silex on 2006-07-07
Have you been using Gconf to edit your settings or another program made to adjust Compiz stuff?  I had the "funky shadow color" problem when I upgraded Compiz once and fixed it by going into Gconf (gconf-editor) and browsing to /apps/compiz/plugins/decoration/allscreens/options and setting shadow_color to #000000

I ended up solving just about all the problems you list in your first post (if you've still got them) somehow by rooting around in Gconf long enough.

Hope you can get your problems fixed.

---

### Post by hotani on 2006-07-07
Thanks for the reply - I'll give that a shot. I've been using the gui tool, gset-compiz to set things but looks like the borders aren't listening to that tool.

EDIT: That did it - thanks!
I had to add the line, but as soon as I did, my shadows were "back in black." Now to poke around in there and see if I can break^W fix some more stuff.

---

### Post by hotani on 2006-07-14
Ok, new install new problems new questions.... 

- Where is the setting to turn off window fading when another has focus?
- I lost my logout options for 'shutdown' and 'restart' - where did they go? I have XGL set up as a session and when I'm using it I'm missing options.
- translucent dragging isn't working

---

### Post by Lunar_Lamp on 2006-07-14
> - Where is the setting to turn off window fading when another has focus?
I have no idea, but if you find it, please say, as this annoys me also.
> 
- I lost my logout options for 'shutdown' and 'restart' - where did they go? I have XGL set up as a session and when I'm using it I'm missing options.
I believe this is a known bug with using this method.  I wrote a little bash script  and created a custom launcher on my panel as a temporary dirty workaround.

```
#!/bin/sh
# for a nice icon use icon from /usr/share/icons/Human/48x48/apps

echo "Type 's' and press enter to shutdown, 'r' and enter to reboot, or any other key to cancel"

read INPUT

if [ "$INPUT" = "s" ]; then
sudo shutdown -h now

elif [ "$INPUT" = "r" ]; then
sudo reboot

else exit

fi

```


> - translucent dragging isn't working
No idea I'm afraid...

---

### Post by mcduck on 2006-07-14
> **hotani said:**
> Ok, new install new problems new questions.... 

- Where is the setting to turn off window fading when another has focus?
- I lost my logout options for 'shutdown' and 'restart' - where did they go? I have XGL set up as a session and when I'm using it I'm missing options.
- translucent dragging isn't working
1. Take a look at the trailfocus plugin. Set minimum opacity to 100 or disable this plugin completely.

2. This is a known issuw when launching XGL as separate session. This far there is no way getting shutdown/restart buttons back.

3. I think setting for this is under move plugin. Just set the minimum opacity to your liking.

If you are using gset-compiz to configure Compiz and can't find those settings, use gconf-editor instead.

---

### Post by hotani on 2006-07-14
Thanks for the replies. When I turn off trailfocus, I lose all window borders so it looks like this one is determined to be running. I'll try messing with the opacity setting when I get home tonight.

I have both opacity settings at '80' for the Move plugin, but still no translucency when moving windows. :(

One more thing.... On other installs I did (this was the first XGL, others have been aiglx) I had the nifty compiz menu at the top (that red cube thingy), but this time it is missing. Any way to add that in? It would be nice because I'm using mythtv and it can't figure out fullscreen mode when compiz is running. The drop-down had a handy "switch to metacity" option in it.

---

### Post by panurge77 on 2006-07-14
The compiz menu is only includade by default in aiglx packages, but you can find a version for xgl con compiz forums
[http://www.compiz.net/viewtopic.php?id=1615](http://www.compiz.net/viewtopic.php?id=1615)

Trailfocus should not be messing with window borders, try realonding compiz if you got problems when you turn it off.
compiz --replace gconf

---

### Post by frigaut on 2006-07-14
Some of the same problem here:
- opacity effects not working anymore while moving windows
- compiz will stubornly not accepts my shortcut to "initiate scale" (the expose effect). Whatever I put in there (I want alt-space), it will ignore the setting. F10 works though (which might be the default setting). I have checked that these entry make it into the /apps/compiz/plugins/scale/screen0/options file; it does, and changes when I do changes thru gset-compiz. I'm scratching my head on this one. This 2 things happened after the recent compiz-quinn013 (?) upgrade. BTW: I'm using Xgl.

---

### Post by hotani on 2006-07-20
I figured out the opacity problem. For some reason gset-compiz is not setting it so you need to use gconf-editor or enable "configuration editor" in the system menu. Go to apps -> compiz -> plugins -> move and set opacity to whatever you want. 

Actually I've found this to be true with several other settings that don't take in gset-compiz. When I set them in gconf-editor they always work.

I still haven't gotten rid of the menus when using mythtv while compiz is running.

---

### Post by richbarna on 2006-07-21
>  2- there is a setting *somewhere* that will turn off the massive annoying bouncing effect when a window is brought to the front, this is different on every machine and I have no idea where the setting is located, other than "somewhere in the wobbly settings."

Anybody find out how to reduce the "Springiness" of the wobbly windows?
I had xgl/compiz installed before on another pc and the  wobbly windows were never this..... wobbly.
They sometimes continue quivering for about 10 seconds.

---

### Post by tukster on 2006-07-21
> **richbarna said:**
> They sometimes continue quivering for about 10 seconds.

open configuration editor
go to apps > compiz > plugins > wobbly
and increase map_friction to 1.7
and map_spring_k to 0.5

---

