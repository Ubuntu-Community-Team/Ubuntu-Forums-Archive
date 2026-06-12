---
title: "XGLsnow, white boxes snowing instead of snowflakes"
date: 2006-12-10
forum: General Help
---

### Post by anasazi on 2006-12-10
I have XGLSnow running however instead of nice snowflakes I have white squares falling to the ground. Any idea on how to fix this?

---

### Post by anasazi on 2006-12-10
> **anasazi said:**
> I have XGLSnow running however instead of nice snowflakes I have white squares falling to the ground. Any idea on how to fix this?

i did this:
> mkdir ~/.beryl/plugins/
ln -sf /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/

and it is no longer boxes, however its not snowflakes.

---

### Post by mcduck on 2006-12-10
try this instead: ```
ln -sf /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/snowflake2.png
```

---

### Post by anasazi on 2006-12-10
No luck. :(

When I turn on textures my square snowflakes go away and it looks like there are really really small dots, maybe a pixel in size, snowing down. They seem to blink.

---

### Post by penguinchrissy on 2006-12-10
I have the same problem I changed the size and they look a little better. I'm also having a problem of when I check snow over windows the snow never goes away. Anyone have this problem.

---

### Post by mcduck on 2006-12-11
> **penguinchrissy said:**
> I have the same problem I changed the size and they look a little better. I'm also having a problem of when I check snow over windows the snow never goes away. Anyone have this problem.

Yes, snow over windows doesn't seem to work yet.. Or it works and works and works...

But the snowflakes look quite good on my machine. If only this plugin would use less CPU, but I suppose it will get better.

---

### Post by hikaricore on 2006-12-11
You can also find more info on the "main" thread for xglsnow here on the beryl forums:

[http://forum.beryl-project.org/viewtopic.php?t=398&postdays=0&postorder=asc&start=0]("http://forum.beryl-project.org/viewtopic.php?t=398&postdays=0&postorder=asc&start=0")

---

### Post by anasazi on 2006-12-11
> **hikaricore said:**
> You can also find more info on the "main" thread for xglsnow here on the beryl forums:

[http://forum.beryl-project.org/viewtopic.php?t=398&postdays=0&postorder=asc&start=0]("http://forum.beryl-project.org/viewtopic.php?t=398&postdays=0&postorder=asc&start=0")

their forum is broken :(

but i did get a chance to read through all 14 pages last night, as far as i could tell some people edited snow.c to change the hard coded size and it fixed the issue but i didn't compile from source. 

so no fix yet :(

i did make it so the snow size is "2" so now i have small snowing boxes that almost look like snow :)

---

### Post by marc_th on 2006-12-12
I'm getting the exact same problem, the plugin does not appear to find/load/use the snowflake image.  I'm using Beryl 0.1.3/xglsnow 0.1.4 on Ubuntu Edgy.  I compiled xglsnow from [this site]("http://cornergraf.net/projects/xglsnow/") and tried messing around with the source code to make sure the it looked for the image under ~/.beryl/plugins/snowflake2.png, to no avail.

Unfortunately, I'm not very strong at programming; does anyone have any idea what's going on?


SNOW_DISPLAY_OPTION_SNOW_TEXTURE_DEFAULT
HOME_IMAGEDIR
SNOWFLAKE_IMAGE
setFileName()
//fileName = SNOW_DISPLAY_OPTION_SNOW_TEXTURE_DEFAULT;

---

### Post by barney_1 on 2006-12-12
I've got my XGLsnow working no problem.

I install the latest svn of beryl from this persons repo:
[Daily Beryl SVN Repo]("http://johnboy45.wordpress.com/2006/11/22/get-always-the-latest-beryl-stuff-in-you-ubuntu-box-without-compiling/")

I made these changes in the terminal:
```
mkdir ~/.beryl/plugins/
ln -sf /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/snowflake2.png
```

Log out, when you log back in you should have snow (this needs to be enabled by check marking "snow" in the left column of the beryl settings.  Press windowskey-F3 to get the show started).

---

### Post by marc_th on 2006-12-12
Thanks for the reply barney_1.  I tried my best to follow your advise without much luck.

1) I completely removed Beryl and emerald via Synaptic Package Manager
2) Removed the Beryl entries in my /etc/apt/sources.list and added:
[LIST]
[*]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
[*]deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
[/LIST]
3) Did an sudo apt-get update
4) Installed all the Beryl/Emerald related packages via Synaptic (including beryl-dev & libberylsettings-dev)
5) deleted ~/.beryl/plugins/ directory
6) did a mkdir ~/.beryl/plugins/
7) Did a ln -sf /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/snowflake2.png
8) Did a Ctrl-Alt-Backspace
9) Did a super-F3

Anyway, now things are better and worse!  I have the latest Subversion (0.1.3+svn20061209-r1629+3v1ubuntu0) installed, which is good because [cornergraf.net]("http://cornergraf.net/projects/xglsnow/") tells us we want the svn version of Beryl installed for xglsnow to work. But is also sucks because now, it's still snowing squares, but not on the workspaces only behind the workspaces when I rotate the screen.  I don't know what to try next? anyone have any ideas?

---

### Post by marc_th on 2006-12-12
Help! My Ubuntu has dandruff!  And all I wanted were snowflakes!

---

### Post by rich.bradshaw on 2006-12-12
hmmm.. mine doesn't work after tips either...

---

### Post by alek66 on 2006-12-12
is there a how to... i saw how to isntalll but how do I set this plug in to work... and how do I set it off i get bored.

---

### Post by marc_th on 2006-12-12
If there is an How-to, I haven't found it yet.  The Beryl Forums had a nice thread, but they've been experiencing issues lately.  The best I've found was reading [cornergraf.net]("http://cornergraf.net/projects/xglsnow/") site carefully and then reading barney_1's post in this thread, which'll lead you to the [Daily Beryl SVN Repo]("http://johnboy45.wordpress.com/2006/11/22/get-always-the-latest-beryl-stuff-in-you-ubuntu-box-without-compiling/").

That's as far as I've gotten, but without much luck.  Beryl forums are back up. I'm going to [look here]("http://forum.beryl-project.org/viewforum.php?f=37") for more info

---

### Post by tmastran on 2006-12-12
I now have the "white box" problem with XGL snow also, on both edgy and dapper, with NVidia. And have a solution / work-around. On both boxes I've been compiling my own Beryl from svn. I played with the code a bit putting in fprintf's in the texture load code and sure enough none were being loaded, even Beryl end caps. SO on a whim I deleted my ~/HOME/.beryl, reinstalled the snow plugin, and it works correctly, displaying textured snow from the image of my choice. Only anomaly is that on dapper while rotating the desktop cube the textures revert to blocks during rotate. Hope this helps.

---

### Post by barney_1 on 2006-12-13
Well, mine is broken with today's beryl build.  I have the white boxes again.  No solution so far.  I couldn't find "snowflake2.png" on my system anymore so I downloaded the plugin, unpacked the png file and had the beryl manager point to it, but not fix yet.

I'll let you know when I find one.

---

### Post by kyldere on 2006-12-13
I also had this working Tuesday, but as of the update today, no luck. Also (I don't know if this is related or not), the splash screen that comes up when Beryl loads does not show up any more ... only a greyed-out screen that indicates that the system is busy (Super + F11 to test). I double-checked to make sure that the paths to the images are correct. Am I alone with this problem? If not, could these be related?

---

### Post by barney_1 on 2006-12-13
I have the same issues with today's build, not splash screen for beryl and white boxes for snowflakes.  It might just be a bad build.  I guess I'll wait and see what tomorrow brings.

---

### Post by jocko on 2006-12-13
I have found a fix. In beryl-manager go to snow and click the "file" tab. At least for me I could see the path was set to /usr/local/somewhere/somewhere/snowflake2.png (don't remember exactly), but I noticed that the file is actually located in /usr/share/beryl/snowflake2.png.

I changed to the correct path and now it works fine.

[COLOR=Red]Edit:[/COLOR] That was apparently not the complete fix. I also activated the new plugins '**[COLOR=Blue]png[/COLOR]**' and 'svg'. It seems like **'png' is required to get beryl to use .png files**.

---

### Post by barney_1 on 2006-12-13
Nice work jocko.

I can confirm that enabling the "png" plugin in beryl-manager and pointing the "snow" plugin to the correct location for snowflake2.png also fixed my problem.

---

### Post by kyldere on 2006-12-13
Turning on the 'png' and 'svc' plugins did the trick. Everything works now. Can you shed any light on why these plugins are now included (and turned off by default?). Thanks again.

---

### Post by alek66 on 2006-12-13
> **marc_th said:**
> Thanks for the reply barney_1.  I tried my best to follow your advise without much luck.

1) I completely removed Beryl and emerald via Synaptic Package Manager
2) Removed the Beryl entries in my /etc/apt/sources.list and added:
[LIST]
[*]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
[*]deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
[/LIST]
3) Did an sudo apt-get update
4) Installed all the Beryl/Emerald related packages via Synaptic (including beryl-dev & libberylsettings-dev)
5) deleted ~/.beryl/plugins/ directory
6) did a mkdir ~/.beryl/plugins/
7) Did a ln -sf /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/snowflake2.png
8) Did a Ctrl-Alt-Backspace
9) Did a super-F3

Anyway, now things are better and worse!  I have the latest Subversion (0.1.3+svn20061209-r1629+3v1ubuntu0) installed, which is good because [cornergraf.net]("http://cornergraf.net/projects/xglsnow/") tells us we want the svn version of Beryl installed for xglsnow to work. But is also sucks because now, it's still snowing squares, but not on the workspaces only behind the workspaces when I rotate the screen.  I don't know what to try next? anyone have any ideas?

i got a 
alek@Darkstar:~/Programas/xglsnow-0.1.4$ make
-e compiling : snow.c -> build/libsnow.loPackage libpng was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libpng', required by 'beryl', not found
/bin/sh: libtool: not found
make: *** [build/libsnow.lo] Error 127

can I install it without the svn repos?

---

### Post by marc_th on 2006-12-13
Awesome jocko.  I too have xglsnow working now.  Unfortunately it's still showing up as boxes when I'm rotating my workspace.  I'll work on trying to find a fix for that tomorrow.

---

### Post by marc_th on 2006-12-13
alek66, I dunno if you can get it working without using the Subversion version of Beryl.  I don't suspect you'll have much luck.

---

### Post by alek66 on 2006-12-13
is there a way to have svn even if i have amd64

---

### Post by anasazi on 2006-12-13
+1 for being fixed in the new version

---

### Post by budman21901 on 2006-12-14
Just downloaded the newest version and i to had the white box problem.  Enabled png and found all the snowflakes in usr/share/beryl

---

### Post by theonhighgod on 2006-12-15
i enabled the png plugin then edited a picture of an actual snowflake, and pointed the plugin at the picture, it works,but the pictures not ideal. Itseems some how i dont have any of the default pictures,atleast i cant find any!

---

### Post by mcduck on 2006-12-15
> **kyldere said:**
> Turning on the 'png' and 'svc' plugins did the trick. Everything works now. Can you shed any light on why these plugins are now included (and turned off by default?). Thanks again.

The idea behind moving image file handling to separate plugins is to make it easier to add support for new image formats, so now instead of changing Beryl core  to support those files developers only need to do a new plugin to handle the image format. I believe are working on a jpg plugin now..

Why they weren't enabled by default is probably just a glitch, this is the unstable development version anyway ;)

---

### Post by prelude6x6 on 2006-12-24
Dunno if you've fixed it yet. But under image format in beryl-manager. PNG must be hooked ;)
hope it works out for you

---

### Post by chadraytay on 2007-01-01
You could try turning on png image loading support like the snow homepage says. Most of the time the white boxes are because you havent got image support loaded/enabled.

---

