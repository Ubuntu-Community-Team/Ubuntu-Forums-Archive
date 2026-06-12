---
title: "[HOWTO]: Extra Compiz Plugins"
date: 2008-06-06
forum: General Help
---

### Post by damis648 on 2008-06-06
I got bored and fed up while installing compiz plugins so i wrote this script to automatically install 12 of them: Anaglyph, Atlantis, Atlantis2, Fireflies, Freewins, Photowheel, Screensaver, Snow, Snowglobe, Stars, Tile, and Wallpaper.
Download the script below.

IMPORTANT NOTES!: DO [COLOR="Red"]NOT[/COLOR] RUN THE SCRIPT AS ROOT AND YOU [COLOR="Red"]MUST[/COLOR] REBOOT AFTER RUNNING THE SCRIPT OR THE PLUGINS WILL NOT FUNCTION PROPERLY.

Tested on Hardy with Compiz 0.7.4.

EDIT: Wow I cannot believe I forgot to upload the script... :popcorn:

**UPDATE: I realized it would do good to update this first post for new versions of the script. The newest version is version 4 on the 4th page.**

---

### Post by damis648 on 2008-06-06
New info: For now, do not enable the wallpaper plugin just yet... there could be a possible flaw in it. I have uploaded an updated script that will not install the wallpaper plugin.

---

### Post by damis648 on 2008-06-06
New News 2: The bug turns out to not be the plugin, but the background manager itself. Continue to use the ORIGINAL script.

---

### Post by damis648 on 2008-06-06
Anybody find this useful? Just wondering.

---

### Post by damis648 on 2008-06-06
No? I just thought maybe some feedback as to plugins to add.

---

### Post by mrsudo on 2008-06-06
works great.... and to think. i thought i already had all the plugins.  
great job.

---

### Post by damis648 on 2008-06-06
Haha you are welcome. :popcorn:

---

### Post by Matthew Wiebelhaus on 2008-06-06
Im testing it right now I will report back when I reboot.

---

### Post by bmwman on 2008-06-06
Are these the same plugins like in Compiz-Git or some new ones? And can I install these if I already have an older version of it?

---

### Post by damis648 on 2008-06-06
These are the ones from compiz-git and as far as i am aware, they should upgrade just fine as they should replace the current files.

---

### Post by damis648 on 2008-06-07
For the record, i HIGHLY recommend the screensaver plugin in flying windows mode. VERY COOL.

---

### Post by damis648 on 2008-06-07
Interesting... does the Freewins (Freely Transformable Windows) plugin not remind anyone of the Matodate application for Windows that used to do this? Just a thought that i remembered.

---

### Post by PatrickFisher on 2008-06-07
> **damis648 said:**
> I got bored and fed up while installing compiz plugins so i wrote this script to automatically install 12 of them: Anaglyph, Atlantis, Atlantis2, Fireflies, Freewins, Photowheel, Screensaver, Snow, Snowglobe, Stars, Tile, and Wallpaper.
Download the script below.

IMPORTANT NOTES!: DO [COLOR="Red"]NOT[/COLOR] RUN THE SCRIPT AS ROOT AND YOU [COLOR="Red"]MUST[/COLOR] REBOOT AFTER RUNNING THE SCRIPT OR THE PLUGINS WILL NOT FUNCTION PROPERLY.

Tested on Hardy with Compiz 0.7.4.

EDIT: Wow I cannot believe I forgot to upload the script... :popcorn:

Sounds cool, I already have the plugins though.

I'm willing to bet that if you hit alt+f2 and run:

```
compiz --replace
```

all of the plugins will work without a restart. For my Elements install script, I just added one more line, and it removed the need for restart. If you're doing it in the script, you'll want to use:

```
compiz --replace &
```


PS: May I suggest using Elements instead of Stars, Snow, and Fireflies? the tarball is at:

[http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)

There's also an install script for it, but you shouldn't need that.

---

### Post by damis648 on 2008-06-08
Ok I will update the script to have elements instead of stars, snow, and fireflies. Thanks for the tip!

EDIT PS: Maybe it was just me but i tried logging out and back in and the plugins did not work so... but i will try the
```
compiz --replace &
```

---

### Post by damis648 on 2008-06-08
The
compiz --replace &
causes a temporary bug in compiz which causes two instances of compiz to run at the same time. Do you think
```
killall compiz
killall compiz.real
compiz --replace &
```
would fix that without a reboot?

---

### Post by unabatedshagie on 2008-06-08
Just tried this and it's working fine for me after rebooting.

Thanks.

---

### Post by Kaneda187 on 2008-06-08
sorry im an idiot

how do i run the script?

---

### Post by Kaneda187 on 2008-06-08
help please

what do i type into the terminal or do i use it or what im an absolute n00b when it comes to the terminal! so I need a idiot proof bit of help

Thanks

---

### Post by Happy_Man on 2008-06-08
Download the script to your desktop and run the following commands one line at a time:

```

cd Desktop
chmod +x compizplugins.sh
./compizplugins.sh

```

---

### Post by Kaneda187 on 2008-06-08
Thank you very much! I will try to remember for next time! thank again!!:)

---

### Post by Kaneda187 on 2008-06-08
I got this error....help?:confused:

kaneda@Kanedas-Interface:~/Desktop$ ./compizplugins.sh
[sudo] password for kaneda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
The following extra packages will be installed:
  libdigest-sha1-perl liberror-perl x11proto-scrnsaver-dev
Suggested packages:
  git-arch git-cvs git-daemon-run git-doc git-email git-gui git-svn gitk
  gitweb
Recommended packages:
  curl
The following NEW packages will be installed:
  git-core libdigest-sha1-perl liberror-perl libglu1-mesa-dev libxss-dev
  x11proto-scrnsaver-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3408kB of archives.
After this operation, 7815kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main x11proto-scrnsaver-dev 1.1.0.0-1 [5204B]
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main libxss-dev 1:1.1.2-1 [15.9kB]
Get:3 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main libdigest-sha1-perl 2.11-2 [24.7kB]
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main liberror-perl 0.17-1 [23.8kB]
Get:5 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main git-core 1:1.5.4.3-1ubuntu2 [3080kB]
Get:6 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy/main libglu1-mesa-dev 7.0.3~rc2-1ubuntu3 [258kB]
Fetched 3408kB in 6s (566kB/s)                                                 
Selecting previously deselected package x11proto-scrnsaver-dev.
(Reading database ... 164877 files and directories currently installed.)
Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.1.0.0-1_all.deb) ...
Selecting previously deselected package libxss-dev.
Unpacking libxss-dev (from .../libxss-dev_1%3a1.1.2-1_i386.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.11-2_i386.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.5.4.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_7.0.3~rc2-1ubuntu3_i386.deb) ...
Setting up x11proto-scrnsaver-dev (1.1.0.0-1) ...
Setting up libxss-dev (1:1.1.2-1) ...
Setting up libdigest-sha1-perl (2.11-2) ...
Setting up liberror-perl (0.17-1) ...
Setting up git-core (1:1.5.4.3-1ubuntu2) ...
Setting up libglu1-mesa-dev (7.0.3~rc2-1ubuntu3) ...
Initialized empty Git repository in /home/kaneda/compiz/anaglyph/.git/
remote: Counting objects: 121, done.
remote: Compressing objects: 100% (117/117), done.
remote: Total 121 (delta 60), reused 0 (delta 0)
Receiving objects: 100% (121/121), 25.88 KiB, done.
Resolving deltas: 100% (60/60), done.
Initialized empty Git repository in /home/kaneda/compiz/atlantis/.git/
remote: Counting objects: 116, done.
remote: Compressing objects: 100% (113/113), done.
remote: Total 116 (delta 70), reused 0 (delta 0)
Receiving objects: 100% (116/116), 50.71 KiB, done.
Resolving deltas: 100% (70/70), done.
Initialized empty Git repository in /home/kaneda/compiz/atlantis2/.git/
remote: Counting objects: 815, done.
remote: Compressing objects: 100% (811/811), done.
remote: Total 815 (delta 557), reused 0 (delta 0)
Receiving objects: 100% (815/815), 2.88 MiB | 571 KiB/s, done.
Resolving deltas: 100% (557/557), done.
Initialized empty Git repository in /home/kaneda/compiz/fireflies/.git/
remote: Counting objects: 51, done.
remote: Compressing objects: 100% (47/47), done.
remote: Total 51 (delta 21), reused 0 (delta 0)
Receiving objects: 100% (51/51), 33.35 KiB, done.
Resolving deltas: 100% (21/21), done.
Initialized empty Git repository in /home/kaneda/compiz/freewins/.git/
remote: Counting objects: 975, done.
remote: Compressing objects: 100% (971/971), done.
remote: Total 975 (delta 669), reused 0 (delta 0)
Receiving objects: 100% (975/975), 228.13 KiB | 326 KiB/s, done.
Resolving deltas: 100% (669/669), done.
Initialized empty Git repository in /home/kaneda/compiz/photowheel/.git/
remote: Counting objects: 32, done.
remote: Compressing objects: 100% (29/29), done.
remote: Total 32 (delta 15), reused 0 (delta 0)
Receiving objects: 100% (32/32), 11.95 KiB, done.
Resolving deltas: 100% (15/15), done.
Initialized empty Git repository in /home/kaneda/compiz/screensaver/.git/
remote: Counting objects: 173, done.
remote: Compressing objects: 100% (169/169), done.
remote: Total 173 (delta 100), reused 0 (delta 0)
Receiving objects: 100% (173/173), 44.50 KiB, done.
Resolving deltas: 100% (100/100), done.
Initialized empty Git repository in /home/kaneda/compiz/snow/.git/
remote: Counting objects: 117, done.
remote: Comprremote: essing objects: 100% (113/113), done.
remote: Total 117 (delta 57), reused 0 (delta 0)
Receiving objects: 100% (117/117), 31.86 KiB, done.
Resolving deltas: 100% (57/57), done.
Initialized empty Git repository in /home/kaneda/compiz/snowglobe/.git/
remote: Counting objects: 99, done.
remote: Compressing objects: 100% (96/96), done.
remote: Total 99 (delta 58), reused 0 (delta 0)
Receiving objects: 100% (99/99), 154.58 KiB, done.
Resolving deltas: 100% (58/58), done.
Initialized empty Git repository in /home/kaneda/compiz/stars/.git/
remote: Counting objects: 20, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 20 (delta 5), reused 0 (delta 0)
Receiving objects: 100% (20/20), 21.47 KiB, done.
Resolving deltas: 100% (5/5), done.
Initialized empty Git repository in /home/kaneda/compiz/tile/.git/
remote: Counting objects: 97, done.
remote: Compressing objects: 100% (94/94), done.
remote: Total 97 (delta 40), reused 0 (delta 0)
Receiving objects: 100% (97/97), 28.43 KiB, done.
Resolving deltas: 100% (40/40), done.
convert   : anaglyph.xml.in -> build/anaglyph.xml
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.h
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.c
schema    : build/anaglyph.xml -> build/compiz-anaglyph.schema
compiling : anaglyph.c -> build/anaglyph.lo
compiling : build/anaglyph_options.c -> build/anaglyph_options.lo
linking   : build/libanaglyph.la
install   : /home/kaneda/.compiz/plugins/libanaglyph.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libanaglyph.so': Permission denied
make: *** [install] Error 1
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : dolphin.c -> build/dolphin.lo
compiling : swim.c -> build/swim.lo
compiling : shark.c -> build/shark.lo
compiling : water.c -> build/water.lo
compiling : whale.c -> build/whale.lo
compiling : atlantis.c -> build/atlantis.lo
compiling : build/atlantis_options.c -> build/atlantis_options.lo
linking   : build/libatlantis.la
install   : /home/kaneda/.compiz/plugins/libatlantis.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libatlantis.so': Permission denied
make: *** [install] Error 1
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : crab.c -> build/crab.lo
compiling : coral.c -> build/coral.lo
compiling : dolphin.c -> build/dolphin.lo
compiling : bfish.c -> build/bfish.lo
compiling : fish.c -> build/fish.lo
compiling : chromis.c -> build/chromis.lo
compiling : swim.c -> build/swim.lo
compiling : float.c -> build/float.lo
compiling : util.c -> build/util.lo
compiling : bubble.c -> build/bubble.lo
compiling : shark.c -> build/shark.lo
compiling : water.c -> build/water.lo
compiling : scuttle.c -> build/scuttle.lo
compiling : whale.c -> build/whale.lo
compiling : atlantis.c -> build/atlantis.lo
compiling : coral2.c -> build/coral2.lo
compiling : fish2.c -> build/fish2.lo
compiling : build/atlantis_options.c -> build/atlantis_options.lo
linking   : build/libatlantis.la
install   : /home/kaneda/.compiz/plugins/libatlantis.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libatlantis.so': Permission denied
make: *** [install] Error 1
convert   : fireflies.xml.in -> build/fireflies.xml
bcop'ing  : build/fireflies.xml -> build/fireflies_options.h
bcop'ing  : build/fireflies.xml -> build/fireflies_options.c
schema    : build/fireflies.xml -> build/compiz-fireflies.schema
compiling : fireflies.c -> build/fireflies.lo
compiling : build/fireflies_options.c -> build/fireflies_options.lo
linking   : build/libfireflies.la
install   : /home/kaneda/.compiz/plugins/libfireflies.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libfireflies.so': Permission denied
make: *** [install] Error 1
convert   : freewins.xml.in -> build/freewins.xml
bcop'ing  : build/freewins.xml -> build/freewins_options.h
bcop'ing  : build/freewins.xml -> build/freewins_options.c
schema    : build/freewins.xml -> build/compiz-freewins.schema
compiling : input.c -> build/input.lo
compiling : action.c -> build/action.lo
compiling : util.c -> build/util.lo
compiling : paint.c -> build/paint.lo
compiling : events.c -> build/events.lo
compiling : freewins.c -> build/freewins.lo
compiling : build/freewins_options.c -> build/freewins_options.lo
linking   : build/libfreewins.la
install   : /home/kaneda/.compiz/plugins/libfreewins.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libfreewins.so': Permission denied
make: *** [install] Error 1
convert   : photo.xml.in -> build/photo.xml
bcop'ing  : build/photo.xml -> build/photo_options.h
bcop'ing  : build/photo.xml -> build/photo_options.c
schema    : build/photo.xml -> build/compiz-photo.schema
compiling : photo.c -> build/photo.lo
compiling : build/photo_options.c -> build/photo_options.lo
linking   : build/libphoto.la
install   : /home/kaneda/.compiz/plugins/libphoto.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libphoto.so': Permission denied
make: *** [install] Error 1
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : wrapper.cpp -> build/wrapper.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : screensaver.cpp -> build/screensaver.lo
compiling : effect.cpp -> build/effect.lo
compiling : vector.cpp -> build/vector.lo
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : matrix.cpp -> build/matrix.lo
compiling : build/screensaver_options.c -> build/screensaver_options.lo
linking   : build/libscreensaver.la
install   : /home/kaneda/.compiz/plugins/libscreensaver.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libscreensaver.so': Permission denied
make: *** [install] Error 1
convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h
bcop'ing  : build/snow.xml -> build/snow_options.c
schema    : build/snow.xml -> build/compiz-snow.schema
compiling : snow.c -> build/snow.lo
compiling : build/snow_options.c -> build/snow_options.lo
linking   : build/libsnow.la
install   : /home/kaneda/.compiz/plugins/libsnow.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libsnow.so': Permission denied
make: *** [install] Error 1
convert   : snowglobe.xml.in -> build/snowglobe.xml
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.h
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.c
schema    : build/snowglobe.xml -> build/compiz-snowglobe.schema
compiling : snowglobe.c -> build/snowglobe.lo
compiling : snowman.c -> build/snowman.lo
compiling : snowflake.c -> build/snowflake.lo
compiling : water.c -> build/water.lo
compiling : movement.c -> build/movement.lo
compiling : build/snowglobe_options.c -> build/snowglobe_options.lo
linking   : build/libsnowglobe.la
install   : /home/kaneda/.compiz/plugins/libsnowglobe.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libsnowglobe.so': Permission denied
make: *** [install] Error 1
convert   : star.xml.in -> build/star.xml
bcop'ing  : build/star.xml -> build/star_options.h
bcop'ing  : build/star.xml -> build/star_options.c
schema    : build/star.xml -> build/compiz-star.schema
compiling : star.c -> build/star.lo
compiling : build/star_options.c -> build/star_options.lo
linking   : build/libstar.la
install   : /home/kaneda/.compiz/plugins/libstar.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libstar.so': Permission denied
make: *** [install] Error 1
convert   : tile.xml.in -> build/tile.xml
bcop'ing  : build/tile.xml -> build/tile_options.h
bcop'ing  : build/tile.xml -> build/tile_options.c
schema    : build/tile.xml -> build/compiz-tile.schema
compiling : tile.c -> build/tile.lo
compiling : build/tile_options.c -> build/tile_options.lo
linking   : build/libtile.la
install   : /home/kaneda/.compiz/plugins/libtile.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libtile.so': Permission denied
make: *** [install] Error 1

---

### Post by Kaneda187 on 2008-06-08
will this cause problems with my compiz?

---

### Post by hAvAAck on 2008-06-08
Worked fine for me, thanks.

---

### Post by damis648 on 2008-06-08
Here is a brand new script that replaces the snow, stars, and fireflies plugin with the elements plugin.

---

### Post by Kaneda187 on 2008-06-08
can anyone help? its something about permission denied ...? Y'all know better than me! please guys help!!

---

### Post by damis648 on 2008-06-08
That is interesting that it would give you this error. I am reading it now and checking. It is a permission problem of some sort... I am not sure what yet though.

---

### Post by Kaneda187 on 2008-06-08
> **damis648 said:**
> That is interesting that it would give you this error. I am reading it now and checking. It is a permission problem of some sort... I am not sure what yet though.
thanks!!

---

### Post by damis648 on 2008-06-08
> **Kaneda187 said:**
> can anyone help? its something about permission denied ...? Y'all know better than me! please guys help!!

Try this next script. It might fix the problem, though I am not 100% sure.

---

### Post by Kaneda187 on 2008-06-08
cd Desktop
kaneda@Kanedas-Interface:~/Desktop$ chmod +x compizplugins.sh
kaneda@Kanedas-Interface:~/Desktop$ ./compizplugins3.sh
bash: ./compizplugins3.sh: Permission denied


got that error when i tried
should i restart and try it?

---

### Post by damis648 on 2008-06-08
Try running it as
```
sh compizplugins3.sh
```

---

### Post by wwuster on 2008-06-11
I ran the script and saw a message go by about cairo-xlib not being found in one of the Makefiles. But most of it seems to have installed. I thought I'd see what 'snow cube' does but can't figure out how to turn it on. If I bring up 'water effect' I see what keys toggle it on and off. How can I connect some keys to the snow cube to see it?

William

---

### Post by Blasphemer on 2008-06-11
I will give this a spin. Thanks you :)

---

### Post by damis648 on 2008-06-11
> **wwuster said:**
> I ran the script and saw a message go by about cairo-xlib not being found in one of the Makefiles. But most of it seems to have installed. I thought I'd see what 'snow cube' does but can't figure out how to turn it on. If I bring up 'water effect' I see what keys toggle it on and off. How can I connect some keys to the snow cube to see it?

William

About the "cairo-xlib" message, this means that Freewins failed to install. If you would like freewins, run the following in terminal:
```
sudo apt-get install libcairo2 libcairo2-dev libcairomm-1.0-1 libcairo-perl libcairo-ruby1.8 libglitz1 libmono-cairo1.0-cil libmono-cairo2.0-cil libpixman-1-0 libpixman-1-dev python-cairo
```
and then re-run the script. I will add these packages to the next script.
As far as the snow cube, that is the snowglobe plugin and is seen when rotating the desktop cube with transparency on.

---

### Post by damis648 on 2008-06-11
I am posting version 4 of the script that should fix any issues about errors regarding cairo-xlib errors.

---

### Post by prshah on 2008-06-11
> **Kaneda187 said:**
> create regular file `/home/kaneda/.compiz/plugins/libatlantis.so': Permission denied
install   : /home/kaneda/.compiz/plugins/libfreewins.soinstall: cannot create regular file `/home/kaneda/.compiz/plugins/libfreewins.so': Permission denied
make: *** [install] Error 1



Looks to me that you already have a ~/.compiz directory/file (why?) to confirm, post output of```

ls -ld ~/.compiz
ls -l ~/.compiz
```

(The first command may give an error if .compiz is not a directory).

---

### Post by Teddy_P on 2008-06-11
I did it and it worked great. Very cool.
I used the compizplugins4.sh 

Thank you
Teddy

---

### Post by colter13 on 2008-06-13
I'm very new to linux and and I don't know how to get this to install. Can you please give me instructions on how to get this to work?

---

### Post by Kaneda187 on 2008-06-13
Check the start of the post, I asked the same question! 

dont forget to say thanks:)

---

### Post by damis648 on 2008-06-13
> **colter13 said:**
> I'm very new to linux and and I don't know how to get this to install. Can you please give me instructions on how to get this to work?

Ha good point ;-). Just right click it, go to permissions, and select executable for all users and groups or check the "allow executing as a program, whichever you see depending on you config. Now just double click the file and select "run in terminal" and that should do it!

---

### Post by easybake on 2008-06-13
Worked perfect. Is there any way you could add the new cube deform and cube reflection. I've tried to get the sphere deformation other ways with no luck.

---

### Post by damis648 on 2008-06-14
> **easybake said:**
> Worked perfect. Is there any way you could add the new cube deform and cube reflection. I've tried to get the sphere deformation other ways with no luck.

I was going to do that but that would require updating to a new unstable version of compiz. I will wait until it becomes stable until I update, and the script cannot be tested if I do not update so I will not include it in the script. (maybe if I find the bugs and they do not apply to me in many ways i might... maybe...)

---

### Post by the lush on 2008-06-16
Hi,

This is a really nice script, thanks! I have found a small problem though andd hope someone might be able to help. 

I enabled one of the extra's (Free Transform Windows - or words to that effect) and now my system refuses to respond to the mouse or keyboard! Even after restarting, although I can move the mouse, I am unable to click on anything, and the keyboard does not respond at all - even the caps lock light does not appear. Has anyone else seen something like this, and if so, is there anyway to fix it without re-installing the entire system?

Thanks in advance for any help.

---

### Post by prshah on 2008-06-16
> **the lush said:**
> 
I enabled one of the extra's (Free Transform Windows - or words to that effect) and now my system refuses to respond to the mouse or keyboard! 
 so, is there anyway to fix it without re-installing the entire system?



I really doubt that it's related to the plugin, but if you're convinced: Boot into recovery mode (select from grub), navigate to your .compiz in your home directory, then delete the offending plugin and restart ```

cd ~/.compiz
rm someplugin
reboot

```

EDIT: The filename is _probably_ freewins

---

### Post by the lush on 2008-06-16
> **prshah said:**
> I really doubt that it's related to the plugin, but if you're convinced: Boot into recovery mode (select from grub), navigate to your .compiz in your home directory, then delete the offending plugin and restart ```

cd ~/.compiz
rm someplugin
reboot

```

I agree, it does seem strange that this would happen, so I suppose it could have been something else, but the timing really was:

1. Enable plug-in
2. Keyboard and Mouse stop working

I am using an ATI Radeon HD3650 GPU, which so far has proven to be a lot more work than the nVidia solution I had in my previous machine.

Thank you so much for your help!

---

### Post by irshadcharm on 2008-06-16
How to install this script? Ive checked the steps already but it gives the following o/p:


```
irshadcharm@irshadcharm-desktop:~/Desktop$ ls

compizplugins4.sh  Sathyaraj & Koundamani  Sathyaraj & Koundamani.torrent

irshadcharm@irshadcharm-desktop:~/Desktop$ chmod +x compizplugins.sh

chmod: cannot access `compizplugins.sh': No such file or directory

irshadcharm@irshadcharm-desktop:~/Desktop$ 

```

---

### Post by Happy_Man on 2008-06-16
Try this ```
./compizplugins4.sh
```

---

### Post by prshah on 2008-06-16
> **irshadcharm said:**
> 
```
irshadcharm@irshadcharm-desktop:~/Desktop$ ls

[color=blue]compizplugins[color=red]4[/color].sh[/color]  Sathyaraj & Koundamani  Sathyaraj & Koundamani.torrent

irshadcharm@irshadcharm-desktop:~/Desktop$ chmod +x [color=blue]compizplugins.sh[/color]

```

You've left out the "4". exact steps:```

cd ~/Desktop
chmod u+x compizplugins4.sh
./compizplugins4.sh

```

OR just:

```

cd ~/Desktop
sh compizplugins4.sh

```

---

### Post by irshadcharm on 2008-06-16
Thanks a lot for the help guys....this is my first hand experience with ubuntu...sorry for my mistake...

---

### Post by damis648 on 2008-06-16
Hello everybody. Sorry I have not checked this thread for a while... On the note of the freewins plugin, has anybody experienced the bug that after rotating a window for a while and then letting go of the mouse button, the desktop starts to move around, following the cursor? This happens continuously on my friend's laptop and once on mine. I will see if I can somehow reproduce it and maybe take a video. Has this happened to anybody else?

EDIT: The video is too large.... i will do it later...

---

### Post by irshadcharm on 2008-06-16
can anyone tell how to uninstall a particular plugin...? im a noob...so detailed answers are welcome...plese help....ive used the compizplugins4.sh script i suppose...also the plugins icons in ccsm are not shown properly...any help would be appreciated...

---

### Post by damis648 on 2008-06-16
> **irshadcharm said:**
> can anyone tell how to uninstall a particular plugin...? im a noob...so detailed answers are welcome...plese help....ive used the compizplugins4.sh script i suppose...also the plugins icons in ccsm are not shown properly...any help would be appreciated...

As far as uninstalling, open a terminal and
```
cd compiz/pluginname/
```
replacing pluginname with the name of the plugin and then
```
sudo make uninstall
``` and it should uninstall.
As far as the icon problem, what do you mean? Could you upload a screenshot?

---

### Post by irshadcharm on 2008-06-16
Thanks for the quick reply bro....im posting the screenshot of my ccsm window...

---

### Post by damis648 on 2008-06-16
> **irshadcharm said:**
> Thanks for the quick reply bro....im posting the screenshot of my ccsm window...

Ah, that just means that these plugins have no icon associated with them. I have it too.

---

### Post by Dutch70 on 2008-06-16
Hi, I would really like to try adding these plug-ins, but I already get an error when I use "compiz --replace" (after disabling it, of course), but as far as I can tell it is working fine. 

Does anyone know what this is, and how to fix it first?

```

david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

 I'd like to get that straightened out then try these plug-ins. 

BTW I am very new to computers and linux! And i am using a 4 month old compaq with 2GB RAM, if that makes a difference.

Edit:
I apologize, I didn't intend to try and make this a help thread for other problems. I didnt want to do it and then be back here looking for support for bigger problems.

---

### Post by elmaster84 on 2008-06-16
Im sorry this is to long. But I did Exactly as you wrote on the thread but it appears no to be working. Ill try to reboot again. 



```
Setting up build-essential (11.3ubuntu1) ...
Initialized empty Git repository in /home/jach/compiz/anaglyph/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/wodor/anaglyph' failed.
Initialized empty Git repository in /home/jach/compiz/atlantis2/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/metastability/atlantis2' failed.
Initialized empty Git repository in /home/jach/compiz/freewins/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/warlock/freewins' failed.
Initialized empty Git repository in /home/jach/compiz/photowheel/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/b0le/photowheel' failed.
Initialized empty Git repository in /home/jach/compiz/screensaver/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/pafy/screensaver' failed.
Initialized empty Git repository in /home/jach/compiz/snowglobe/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/metastability/snowglobe' failed.
Initialized empty Git repository in /home/jach/compiz/tile/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/tile' failed.
Initialized empty Git repository in /home/jach/compiz/wallpaper/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/wallpaper' failed.
./compizplugins4.sh: line 16: cd: anaglyph: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 20: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 24: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 28: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 32: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 36: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 40: cd: tile: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 44: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `elements': Permission denied
./compizplugins4.sh: line 49: cd: elements: No such file or directory
--16:32:31--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `elements-most-recent.tar.gz'
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 118,200 (115K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

```

HELP needed!!!

---

### Post by damis648 on 2008-06-16
> **elmaster84 said:**
> Im sorry this is to long. But I did Exactly as you wrote on the thread but it appears no to be working. Ill try to reboot again. 



```
Setting up build-essential (11.3ubuntu1) ...
Initialized empty Git repository in /home/jach/compiz/anaglyph/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/wodor/anaglyph' failed.
Initialized empty Git repository in /home/jach/compiz/atlantis2/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/metastability/atlantis2' failed.
Initialized empty Git repository in /home/jach/compiz/freewins/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/warlock/freewins' failed.
Initialized empty Git repository in /home/jach/compiz/photowheel/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/b0le/photowheel' failed.
Initialized empty Git repository in /home/jach/compiz/screensaver/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/pafy/screensaver' failed.
Initialized empty Git repository in /home/jach/compiz/snowglobe/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/users/metastability/snowglobe' failed.
Initialized empty Git repository in /home/jach/compiz/tile/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/tile' failed.
Initialized empty Git repository in /home/jach/compiz/wallpaper/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=No route to host
fatal: unable to connect a socket (No route to host)
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/wallpaper' failed.
./compizplugins4.sh: line 16: cd: anaglyph: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 20: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 24: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 28: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 32: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 36: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 40: cd: tile: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 44: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `elements': Permission denied
./compizplugins4.sh: line 49: cd: elements: No such file or directory
--16:32:31--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `elements-most-recent.tar.gz'
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 118,200 (115K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

```

HELP needed!!!

It would seem that git cannot connect to the internet.. interesting. You are connected when running the script?

---

### Post by damis648 on 2008-06-16
> **Dutch70 said:**
> Hi, I would really like to try adding these plug-ins, but I already get an error when I use "compiz --replace" (after disabling it, of course), but as far as I can tell it is working fine. 

Does anyone know what this is, and how to fix it first?

```

david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

 I'd like to get that straightened out then try these plug-ins. 

BTW I am very new to computers and linux! And i am using a 4 month old compaq with 2GB RAM, if that makes a difference.

Edit:
I apologize, I didn't intend to try and make this a help thread for other problems. I didnt want to do it and then be back here looking for support for bigger problems.

That is fine. If I were you, try using the scale plugin. If it still works, then you should be fine.

---

### Post by elmaster84 on 2008-06-17
> It would seem that git cannot connect to the internet.. interesting. You are connected when running the script? 

Yes, I was on class when I tried and my collage has free wireless. While I was running the script I also surfed the web.

Is it ok for me to try and run the script again?

---

### Post by irshadcharm on 2008-06-17
> **damis648 said:**
> Ah, that just means that these plugins have no icon associated with them. I have it too.

Since im new to linux...can u guide me how to setup these plugins to get a nice effect in my ubuntu machine...i donno how to setup these plugins....any help wud be appreciated...ive read the forlong's blog to setup some of my plugins...but i wanna real eye candy...and is there anyway to automatically update these compiz plugins...?waiting for ur reply...

---

### Post by damis648 on 2008-06-17
> **elmaster84 said:**
> Yes, I was on class when I tried and my collage has free wireless. While I was running the script I also surfed the web.

Is it ok for me to try and run the script again?

That would be perfectly ok.

---

### Post by damis648 on 2008-06-17
> **irshadcharm said:**
> Since im new to linux...can u guide me how to setup these plugins to get a nice effect in my ubuntu machine...i donno how to setup these plugins....any help wud be appreciated...ive read the forlong's blog to setup some of my plugins...but i wanna real eye candy...and is there anyway to automatically update these compiz plugins...?waiting for ur reply...

Alright, sure.

Anaglyph - Enable it by checking the box. You can check the bindings by going into the settings of it, but Alt+Super+S will toggle it on the screen. It makes a nice effect if you have some 3d glasses lying around.

Cube Atlantis will show an aquarium in the desktop cube, if you have it transparent and enabled.

Cube Snow Globe wil do the same, but have a snowglobe.

Freely Transformable windows is used with Shift+Ctrl+Left Mouse button to freely move a window. You may also use the right mouse button to scale a window. Reset them using Shift+Ctrl+R.

Photowheel will display photo textures in your transparent cube. Specify them in the configuration.

Elements will display falling leaves, snow, fireflies, or a starfield on your desktop. Check all the bindings in the settings, for there are many.

The Screensaver is my favorite. Once enabled, you can set the time to activate and the mode to use. In flying windows mode, it will have the windows fly around with your cube skydome as your background. In cube mode, it will simply show your spinning cube.

---

### Post by SteveNorman on 2008-06-19
I removed compiz after a failed compiz-git attempt. Should I load compiz from synaptic first or can I just use your script for the whole thing?

---

### Post by damis648 on 2008-06-19
You will have to install compiz from synaptic first. Then this script will install the extra plugins listed on the first page.

---

### Post by SteveNorman on 2008-06-19
oh gottcha,,thanks!

---

### Post by damis648 on 2008-06-19
Welcome!

---

### Post by Victormd on 2008-06-20
You said that you didn't want to add the cube reflection and deformation because it would require you to update to an unstable version of compiz, and I agree with you. But I've got some time on my hands and wanted to try to get it working... Since you seem to be the expert and I've never installed it other than from the repos, any suggestions/tips/links?

---

### Post by damis648 on 2008-06-20
> **Victormd said:**
> You said that you didn't want to add the cube reflection and deformation because it would require you to update to an unstable version of compiz, and I agree with you. But I've got some time on my hands and wanted to try to get it working... Since you seem to be the expert and I've never installed it other than from the repos, any suggestions/tips/links?

Oh, beleive me, I am not the expert, I am 13. I was just bored. :popcorn: What I have found out however is basic instructions on how to install compiz-fusion from git. Here are some links:

Oh wow, In the process of trying to find these pages again, I stumbled across this: [http://status.compiz-fusion.org/](http://status.compiz-fusion.org/)
Perhaps updating might not be such a bad idea...

Anyway, here are the links if you are interested:
[http://translate.google.com/translate?u=http%3A%2F%2Ftelperion.wordpress.com%2F2008%2F03%2F10%2Fcompizfusion-makefusion9-script-per-compilazione%2F&langpair=it|en&hl=it&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Ftelperion.wordpress.com%2F2008%2F03%2F10%2Fcompizfusion-makefusion9-script-per-compilazione%2F&langpair=it|en&hl=it&ie=UTF-8)
[http://ubuntuforums.org/showthread.php?t=643485](http://ubuntuforums.org/showthread.php?t=643485) < That is a guide for it
[http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218) < That is a pre-written script that will update from git.

---

### Post by kk0sse54 on 2008-06-20
Very cool, so far it works for me

---

### Post by damis648 on 2008-06-20
> **C!oud said:**
> Very cool, so far it works for me

Glad to know!

---

### Post by Victormd on 2008-06-21
Got it working... I still have to play around with it a bit but the links you provided did the trick. Actually I had already seen one of them but thought it was too old and was trying to find a more up-to-date thread, but I guess it's pretty general and a few modifications and it did the trick for me (and what I wanted).
I'm posting a snapshot just to show the deformation at work, very cool!

---

### Post by Victormd on 2008-06-21
Ok... after playing around with it a little bit, here's what I've found:
(please keep in mind that this is not using the script provided by the op of this thread, these are comments on the unstable version for those who decide to give it a shot).
Pros:
1. The effects are awesome and there are lots of them.
Cons:
1. I don't like the fact that I have to have the Compiz Fusion Icon setup to start under sessions;
2. I don't like the fact that I have to use the Compiz Fusion Icon at all (I've never had to use it before). If not used, then ccsm will not commit the changes;
3. I have a pretty good graphics card but after a while, specially with the deformation plugin, it just got really... but I mean really slugish (started the rotation, then it became slugish, went to the kitchen to get a cup of coffee, came back and it was still returning to the original position of the cylinder).

---

### Post by damis648 on 2008-06-21
> **Victormd said:**
> Ok... after playing around with it a little bit, here's what I've found:
(please keep in mind that this is not using the script provided by the op of this thread, these are comments on the unstable version for those who decide to give it a shot).
Pros:
1. The effects are awesome and there are lots of them.
Cons:
1. I don't like the fact that I have to have the Compiz Fusion Icon setup to start under sessions;
2. I don't like the fact that I have to use the Compiz Fusion Icon at all (I've never had to use it before). If not used, then ccsm will not commit the changes;
3. I have a pretty good graphics card but after a while, specially with the deformation plugin, it just got really... but I mean really slugish (started the rotation, then it became slugish, went to the kitchen to get a cup of coffee, came back and it was still returning to the original position of the cylinder).

I am considering updating but cons you described are changing my mind a bit... Well I am glad that I could help with the links! Have fun!

---

### Post by Victormd on 2008-06-21
Yeah, I regret updating at this point... Don't really think it was my best choice (especially because it was working very well before) but I was not expecting the loss in performance, especially with my graphics card.

---

### Post by Victormd on 2008-06-21
Anyone know how to avoid having to manually reload the window manager? This is minor but still, really anoying... the weird thing is that AWN will only show up after I reload the window manager (through fusion-icon)

---

### Post by Victormd on 2008-06-22
Ok, just an update...
After about three unsuccesful attempts to remove the updated compiz and revert to the repository version, I totally wiped compiz+directories and everything compiz related and installed the updated version again (I couldn't get the original to work). Now everything is working fine! I still have to load fusion-icon at startup but don't have to reload window manager anymore.

I did notice that sometimes it doesn't like amarok too much, It will momentarily screw up the display if amarok is running. I haven't noticed this with any other application.

[COLOR="Blue"]**damis648**, this is something you might consider in a new script, adding a conditional statement asking if the user would like to completely remove compiz + compiz settings before installing the updated version.[/COLOR]

---

### Post by damis648 on 2008-06-22
> **Victormd said:**
> Ok, just an update...
After about three unsuccesful attempts to remove the updated compiz and revert to the repository version, I totally wiped compiz+directories and everything compiz related and installed the updated version again (I couldn't get the original to work). Now everything is working fine! I still have to load fusion-icon at startup but don't have to reload window manager anymore.

I did notice that sometimes it doesn't like amarok too much, It will momentarily screw up the display if amarok is running. I haven't noticed this with any other application.

[COLOR="Blue"]**damis648**, this is something you might consider in a new script, adding a conditional statement asking if the user would like to completely remove compiz + compiz settings before installing the updated version.[/COLOR]

Thanks for the update, I will consider it!

---

### Post by evanwolves999 on 2008-06-24
Hello everyone, this is my first post so please don't get mad at me if I ask a question that has already been asked a million times.  I just had a few questions that I could not find exact answers to in the forums.

1.  what exactly does git mean?  I know these extra plug-ins are not natively supported but I can only find compiz not compiz git so what is the deal? 

2.  Is there a solution to the flying windows screensaver or is it currently broken?  It seems that if I set the time to .1000 it works fine but if it is set to 5 then it does not work.  

3.  How are people totally messing up compiz?  And if this occurs then how do people get back to the original settings?  Someone that was experimenting with unstable add ons mentioned uninstalling and reinstalling, but he still has to mess with the icon.  This does not seem like a total solution to me so...can this be fixed or do you just have to reinstall ubuntu?  

Thank you in advance for everyone's help.

---

### Post by Happy_Man on 2008-06-24
> **evanwolves999 said:**
> Hello everyone, this is my first post so please don't get mad at me if I ask a question that has already been asked a million times.  I just had a few questions that I could not find exact answers to in the forums.

1.  what exactly does git mean?  I know these extra plug-ins are not natively supported but I can only find compiz not compiz git so what is the deal? 

2.  Is there a solution to the flying windows screensaver or is it currently broken?  It seems that if I set the time to .1000 it works fine but if it is set to 5 then it does not work.  

3.  How are people totally messing up compiz?  And if this occurs then how do people get back to the original settings?  Someone that was experimenting with unstable add ons mentioned uninstalling and reinstalling, but he still has to mess with the icon.  This does not seem like a total solution to me so...can this be fixed or do you just have to reinstall ubuntu?  

Thank you in advance for everyone's help.
1. Git is a program that enables the user to download the current development version that, as in cases like Compiz, are snazzier and more stable but at the cost of being untested. It's not a repo, it comes as source code to be compiled, although some people host repos and convert the code to .deb files for you. If you use one of these repos, chances are that the new*est* features have not been incorporated, but it's still light-years ahead of the stable releases that distro maintainers tend to ship, so I suggest you use one of those unless you really need/want a new feature that's only available in the git directory.

2. That I don't have the answer to. Sorry.

3. There are many ways to mess up Compiz, either by somehow conflicting plugins (you've seen the settings manager, not every single configuration scheme can be tested before shipping, nor is it advisable to do so), or from inconsistencies with the drivers for the video card. ATi is a big culprit, as their drivers, for the time being, suck balls, and so they are very unstable on their own, without the added strain of running Compiz, especially on older cards. Other times, it's a problem with the driver not communicating or miscommunicating with the motherboard or X (the program that provides a base for the GUI). There are many ways to mess up Compiz/your computer.
Now to fix it, it's usually best to just delete the ~/.compiz/compizconfig folder. This resets your settings by forcing the settings manager to remake a default settings folder the next time you start it up. Be careful to do that *with Compiz off*, for obvious reasons.

---

### Post by duncanyoyo1 on 2008-06-24
Well, I instaled and at the end it says "destination directory 'anaglyph' already exists.
destination directory 'atlantis2' already exists.
destination directory 'freewins' already exists.
destination directory 'photowheel' already exists.
Initialized empty Git repository in /home/duncanyoyo1/compiz/screensaver/.git/" But the "Initialized empty Git repository" is always a different plugin. 

How can I get this to work?

( I am on Ubuntu 8.04 )

Nevermind the Alt+F2 method worked for me.

But I seem to be missing a few plugins like the Sphere and Cylinder, and more =\

---

### Post by jessica19 on 2008-06-25
I tried latest version 4 and it wouldn't work for me.But  I tried version 3 and it works fine. Thanks alot! Ubuntu Hardy 8.0.4

---

### Post by Victormd on 2008-06-25
> **evanwolves999 said:**
> 3.  How are people totally messing up compiz?  And if this occurs then how do people get back to the original settings?  Someone that was experimenting with unstable add ons mentioned uninstalling and reinstalling, but he still has to mess with the icon.  This does not seem like a total solution to me so...can this be fixed or do you just have to reinstall ubuntu?

I was "one of those people" and after my last failed attempt to downgrade from compiz-git to the repository version, and reinstalling compiz-git, everything is working fine (as I stated on a previous post) and the fusion-icon, though loaded, does not need to be tempered with anymore.

What I did was completely removed any traces of compiz (folders, config files, removed from synaptic as they were still marked as installed even though they weren't), and reinstalled compiz-git and all is well in the fusion land! :)

---

### Post by Victormd on 2008-06-25
> **duncanyoyo1 said:**
> 
But I seem to be missing a few plugins like the Sphere and Cylinder, and more =\

Yeah, the sphere and cylinder plugins are not part of this script, but if you'd like to install it, here's how:
open a terminal window and create a folder for the additional plugins (you can call it anything you'd like)
```
mkdir ~/compiz-plugins
```
```
cd ~/compiz-plugins
```
Download the cube reflection and deformation plugin (sphere and cylinder)
```
git-clone git://gitweb.beryl-project.org/fusion/plugins/cubeaddon
```
```
cd cubeaddon
```
```
make
```
```
sudo make install
```

These two last lines are valid for any plugins you download from the above link as long as you're in the right folder.
For additional plugins, visit [http://gitweb.beryl-project.org/](http://gitweb.beryl-project.org/)

---

### Post by tornado89 on 2008-06-25
it's gr8 but i had errors in couple of effects while compiling
and they've not been added to the effects options

---

### Post by Victormd on 2008-06-25
You can download them from the [gitweb link]("http://gitweb.beryl-project.org/") and install following the instructions I posted earlier.

---

### Post by duncanyoyo1 on 2008-06-25
This may be the wrong topic ( seeing as there is a topic about installing compiz from git ) But I recently installed compiz from git, and it didnt go so well, I didn't get errors or anything, but there where no window decorations and none of the effects worked, so I uninstalled everything.
Here is a list of things I uninstalled


bcop
ccsm
libcompizconfig
compizconfig-python
plugins-main
plugins-extra
plugins-unsupported
emerald

And now when I try to reinstall compiz fusion, it doesnt work, I have the same problem as before, no window decorations. What can I do to get compiz working?

I see you deleted everything to do with compiz and then reinstalled from git. Would you suggest that? ( I would like to get compiz fusion from Git ) And if it is what you suggest what is a good guide to install compiz fusion from git?

---

### Post by Victormd on 2008-06-25
Ultimately, this is what I did:
remove compiz and dependencies from synaptics:
```
sudo apt-get remove libcompiz* compiz* compiz compizconfig-backend-gconf compizconfig-backend-kconfig libdecoration0 compizconfig-settings-manager python-compizconfig emerald
```
Remove all compiz related files (you can copy and paste all of these lines at once):
```
sudo rm -rf /etc/compiz* > /dev/null 2>&1
sudo rm -rf /etc/xdg/compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.gconf/apps/compiz* > /dev/null 2>&1
sudo rm -rf /root/.compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm -rf /usr/local/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/local/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/local/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/local/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/local/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/local/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/local/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm /usr/local/share/locale/*/LC_MESSAGES/*compiz*.mo > /dev/null 2>&1
sudo rm /usr/share/locale-langpack/*/LC_MESSAGES/compiz* > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.so > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.a > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.la > /dev/null 2>&1
sudo rm /usr/local/lib/python2.5/site-packages/compiz* > /dev/null 2>&1
```
Remove Compiz-git
```
sudo apt-get remove compiz-git
sudo mv /etc/apt/sources.list /etc/apt/sources.list1
sudo apt-get update
sudo cp /etc/apt/sources.list1 /etc/apt/sources.list
sudo apt-get update
```
[source]("http://ubuntuforums.org/showthread.php?t=781218&page=2")

Reinstall following [this guide]("http://ubuntuforums.org/showthread.php?t=781218").

---

### Post by phoenixankit on 2008-06-26
> **Victormd said:**
> You can download them from the [gitweb link]("http://gitweb.beryl-project.org/") and install following the instructions I posted earlier.

How do I download from there? I can see the things I want, but all links lead to something other than 'download'

---

### Post by enyckma on 2008-06-26
for the "Window Previews" plugin 

can you add a button to preview the window even if this is minimized?

---

### Post by borlosky on 2008-06-28
> **damis648 said:**
> I got bored and fed up while installing compiz plugins so i wrote this script to automatically install 12 of them: Anaglyph, Atlantis, Atlantis2, Fireflies, Freewins, Photowheel, Screensaver, Snow, Snowglobe, Stars, Tile, and Wallpaper.
Download the script below.

IMPORTANT NOTES!: DO [COLOR="Red"]NOT[/COLOR] RUN THE SCRIPT AS ROOT AND YOU [COLOR="Red"]MUST[/COLOR] REBOOT AFTER RUNNING THE SCRIPT OR THE PLUGINS WILL NOT FUNCTION PROPERLY.

Tested on Hardy with Compiz 0.7.4.

EDIT: Wow I cannot believe I forgot to upload the script... :popcorn:

**UPDATE: I realized it would do good to update this first post for new versions of the script. The newest version is version 4 on the 4th page.**

so now that i have that script, how do i get it to install? sorry I'm a newb when it comes to linux :-(

---

### Post by blondebeard on 2008-06-28
hey i just wanted to say thanx for this i couldnt compile most of them my self but you script is fail safe. thanx alot man

---

### Post by Llewxam on 2008-06-28
anyone know how i can get the cubeaddon on gutsy? my compiz version is compiz 0.6.3
my question is, is it even possible? would like that last plugin without the need to upgrade to hardy.

---

### Post by Victormd on 2008-06-29
I believe it's only compatible with 0.7.x so you won't be able to use it in Hardy.

---

### Post by Victormd on 2008-06-29
> **phoenixankit said:**
> How do I download from there? I can see the things I want, but all links lead to something other than 'download'

you download from the terminal using the "git" command:
```
git-clone git://**gitweb.beryl-project.org/fusion/plugins/cubeaddon**
```
replacing the link with the one corresponding to what you want. Please note that, if you copy the link from your browser, it won't work. You have to copy the list name. Let's say you want to download the atlantis plugin. If you click on the link in the gitweb.beryl-project.org site, you'll get something like this in the browser link:
> [http://gitweb.beryl-project.org/?p=](http://gitweb.beryl-project.org/?p=)**fusion/plugins/atlantis**;a=summary
but all you need is the part in bold so the command would look like this:
```
git-clone git://**gitweb.beryl-project.org/fusion/plugins/atlantis**
```
Hope this helps.

---

### Post by hackerseraph on 2008-06-29
anyone else notice after running this that they cant draw water on the screen anymore? both my water and my draw on screen plugins are missing :( anyone know how to get them back?

---

### Post by Llewxam on 2008-06-29
> **Victormd said:**
> I believe it's only compatible with 0.7.x so you won't be able to use it in Hardy.

dang. would've been happy with that plugin... oh well.

---

### Post by borlosky on 2008-06-29
> **damis648 said:**
> Try this next script. It might fix the problem, though I am not 100% sure.

after running this script, i no longer have a title bar on any windows, i can't move windows, or minimize, or close, please help. here's a screenshot:

[http://i29.photobucket.com/albums/c282/borlosky/Screenshot.png](http://i29.photobucket.com/albums/c282/borlosky/Screenshot.png)



EDIT: never mind, reboot fixed the problem, but the extra plugins still not present in my compiz settings manager

---

### Post by Chonnawonga on 2008-06-29
New effects work very well. Thanks for the script!

Tried to install the cubeaddon plugin, but got this series of errors on "make":

```
compiling : cubeaddon.c -> build/cubeaddon.locubeaddon.c:77: error: expected specifier-qualifier-list before ‘CubeShouldPaintViewportProc’
cubeaddon.c: In function ‘cubeaddonChangeCap’:
cubeaddon.c:238: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c:238: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c: In function ‘cubeaddonTopImagesChanged’:
cubeaddon.c:270: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c:271: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c: In function ‘cubeaddonBottomImagesChanged’:
cubeaddon.c:285: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c:286: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c: In function ‘cubeaddonCheckOrientation’:
cubeaddon.c:464: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c: In function ‘cubeaddonGetRotation’:
cubeaddon.c:483: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c:485: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:489: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c: In function ‘cubeaddonClearTargetOutput’:
cubeaddon.c:500: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c:504: error: ‘CubeaddonScreen’ has no member named ‘backVRotate’
cubeaddon.c:507: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c: In function ‘cubeaddonShouldPaintViewport’:
cubeaddon.c:523: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:523: error: ‘CubeaddonScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:524: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeaddonScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:531: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:560: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c: In function ‘cubeaddonPaintCap’:
cubeaddon.c:632: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c:638: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c:650: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:659: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:659: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:702: error: ‘CubeaddonScreen’ has no member named ‘capFillIdx’
cubeaddon.c:766: error: ‘CubeaddonScreen’ has no member named ‘capFillIdx’
cubeaddon.c:770: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c: In function ‘cubeaddonPaintTop’:
cubeaddon.c:802: error: ‘CubeaddonScreen’ has no member named ‘paintTop’
cubeaddon.c:804: error: ‘CubeaddonScreen’ has no member named ‘paintTop’
cubeaddon.c: In function ‘cubeaddonPaintBottom’:
cubeaddon.c:831: error: ‘CubeaddonScreen’ has no member named ‘paintBottom’
cubeaddon.c:833: error: ‘CubeaddonScreen’ has no member named ‘paintBottom’
cubeaddon.c: In function ‘cubeaddonAddWindowGeometry’:
cubeaddon.c:856: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:907: error: ‘CubeaddonScreen’ has no member named ‘tmpRegion’
cubeaddon.c:909: error: ‘CubeaddonScreen’ has no member named ‘tmpRegion’
cubeaddon.c:912: error: ‘CubeaddonScreen’ has no member named ‘tmpRegion’
cubeaddon.c:924: error: ‘CubeaddonScreen’ has no member named ‘nTmpBox’
cubeaddon.c:926: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:926: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:927: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:929: error: ‘CubeaddonScreen’ has no member named ‘nTmpBox’
cubeaddon.c:933: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:981: error: ‘CubeaddonScreen’ has no member named ‘last’

cubeaddon.c:982: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:984: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:985: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1028: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1072: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1073: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c: In function ‘cubeaddonDrawWindow’:
cubeaddon.c:1102: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c: In function ‘cubeaddonDrawWindowTexture’:
cubeaddon.c:1138: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1152: error: ‘CubeaddonScreen’ has no member named ‘winNormSize’
cubeaddon.c:1154: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1154: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1156: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1158: error: ‘CubeaddonScreen’ has no member named ‘winNormSize’
cubeaddon.c:1161: error: ‘CubeaddonScreen’ has no member named ‘winNormSize’
cubeaddon.c:1181: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1182: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1184: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1185: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1219: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1219: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1220: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1220: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1221: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1225: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1225: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1226: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1226: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1227: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1234: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c: In function ‘cubeaddonPaintTransformedOutput’:
cubeaddon.c:1271: error: ‘CubeaddonScreen’ has no member named ‘wasDeformed’
cubeaddon.c:1277: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1282: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1300: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1307: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1309: error: ‘CubeaddonScreen’ has no member named ‘capDistance’
cubeaddon.c:1315: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1315: error: ‘CubeaddonScreen’ has no member named ‘capDeform’
cubeaddon.c:1315: error: ‘CubeaddonScreen’ has no member named ‘capDistance’
cubeaddon.c:1316: error: ‘CubeaddonScreen’ has no member named ‘capDeformType’
cubeaddon.c:1326: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1327: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1328: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1329: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1330: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1331: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1339: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1343: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1349: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1360: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1361: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1361: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1362: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1363: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1364: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1365: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1378: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1380: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1382: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1389: error: ‘CubeaddonScreen’ has no member named ‘capFillNorm’
cubeaddon.c:1399: error: ‘CubeaddonScreen’ has no member named ‘capDeform’
cubeaddon.c:1399: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1400: error: ‘CubeaddonScreen’ has no member named ‘capDistance’
cubeaddon.c:1401: error: ‘CubeaddonScreen’ has no member named ‘capDeformType’
cubeaddon.c:1404: error: ‘CubeaddonScreen’ has no member named ‘first’
cubeaddon.c:1406: error: ‘CubeaddonScreen’ has no member named ‘first’
cubeaddon.c:1407: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c:1439: error: ‘CubeaddonScreen’ has no member named ‘backVRotate’
cubeaddon.c:1461: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1462: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1463: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1464: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1484: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1498: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1506: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1506: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1507: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1512: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1517: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1527: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1530: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1533: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1537: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1540: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1542: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1543: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1545: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1547: error: ‘CubeaddonScreen’ has no member named ‘backVRotate’
cubeaddon.c:1547: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1551: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1551: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1552: error: ‘CubeaddonScreen’ has no member named ‘capFill’
cubeaddon.c:1556: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1569: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1572: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1576: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1599: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1603: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1603: error: ‘CubeaddonScreen’ has no member named ‘vRot’
cubeaddon.c:1665: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c:1670: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1671: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1672: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1675: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1675: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c: In function ‘cubeaddonPaintOutput’:
cubeaddon.c:1695: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1696: error: ‘CubeaddonScreen’ has no member named ‘first’
cubeaddon.c:1698: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c: In function ‘cubeaddonDonePaintScreen’:
cubeaddon.c:1712: error: ‘CubeaddonScreen’ has no member named ‘first’
cubeaddon.c:1713: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1714: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1716: error: ‘CubeaddonScreen’ has no member named ‘wasDeformed’
cubeaddon.c:1716: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1718: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1718: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1721: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c: In function ‘cubeaddonInitScreen’:
cubeaddon.c:1799: error: ‘CubeaddonScreen’ has no member named ‘reflection’
cubeaddon.c:1800: error: ‘CubeaddonScreen’ has no member named ‘first’
cubeaddon.c:1801: error: ‘CubeaddonScreen’ has no member named ‘last’
cubeaddon.c:1802: error: ‘CubeaddonScreen’ has no member named ‘yTrans’
cubeaddon.c:1803: error: ‘CubeaddonScreen’ has no member named ‘zTrans’
cubeaddon.c:1804: error: ‘CubeaddonScreen’ has no member named ‘tmpRegion’
cubeaddon.c:1805: error: ‘CubeaddonScreen’ has no member named ‘deform’
cubeaddon.c:1806: error: ‘CubeaddonScreen’ has no member named ‘capDeform’
cubeaddon.c:1807: error: ‘CubeaddonScreen’ has no member named ‘capDistance’
cubeaddon.c:1809: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1810: error: ‘CubeaddonScreen’ has no member named ‘winNormSize’
cubeaddon.c:1812: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:1813: error: ‘CubeaddonScreen’ has no member named ‘nTmpBox’
cubeaddon.c:1815: error: ‘CubeaddonScreen’ has no member named ‘capFillIdx’
cubeaddon.c:1828: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c:1829: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c:1831: error: ‘CubeaddonScreen’ has no member named ‘topCap’
cubeaddon.c:1832: error: ‘CubeaddonScreen’ has no member named ‘bottomCap’
cubeaddon.c:1858: error: ‘CubeaddonScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:1858: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:1858: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:1859: error: ‘CubeaddonScreen’ has no member named ‘paintTop’
cubeaddon.c:1860: error: ‘CubeaddonScreen’ has no member named ‘paintBottom’
cubeaddon.c: In function ‘cubeaddonFiniScreen’:
cubeaddon.c:1872: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1873: error: ‘CubeaddonScreen’ has no member named ‘winNormals’
cubeaddon.c:1875: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:1876: error: ‘CubeaddonScreen’ has no member named ‘tmpBox’
cubeaddon.c:1878: error: ‘CubeaddonScreen’ has no member named ‘tmpRegion’
cubeaddon.c:1890: error: ‘CubeScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:1890: error: ‘CubeaddonScreen’ has no member named ‘shouldPaintViewport’
cubeaddon.c:1891: error: ‘CubeaddonScreen’ has no member named ‘paintTop’
cubeaddon.c:1892: error: ‘CubeaddonScreen’ has no member named ‘paintBottom’
make: *** [build/cubeaddon.lo] Error 1

```

---

### Post by borlosky on 2008-07-02
after trying again, options are now in my compiz settings manager, but when i try to select the new plugins, the option only stays checked for about 2 seconds, then check mark disappears. all original plugins still work fine. only having the problem with the new plugins (snow, snow globe, screen saver, atlantis ect...)

---

### Post by tynen on 2008-07-02
I'm going to try it when I get home (at the office with windows :( )

---

### Post by damis648 on 2008-07-05
> **borlosky said:**
> after trying again, options are now in my compiz settings manager, but when i try to select the new plugins, the option only stays checked for about 2 seconds, then check mark disappears. all original plugins still work fine. only having the problem with the new plugins (snow, snow globe, screen saver, atlantis ect...)

Sorry, I have not checked this thread in a while. Now, what version of compiz do you have?

> New effects work very well. Thanks for the script!

Tried to install the cubeaddon plugin, but got this series of errors on "make":

This is because this plugin will only work on compiz .7.5 or higher.

---

### Post by borlosky on 2008-07-05
> **damis648 said:**
> Sorry, I have not checked this thread in a while. Now, what version of compiz do you have?



This is because this plugin will only work on compiz .7.5 or higher.

I'm using 0.7.7

---

### Post by damis648 on 2008-07-05
> **borlosky said:**
> I'm using 0.7.7

Interesting... I am sorry I cannot be of further help, as I have never personally compiled this. Try googling the errors. I am sure you will find something.

---

### Post by borlosky on 2008-07-05
> **damis648 said:**
> Interesting... I am sorry I cannot be of further help, as I have never personally compiled this. Try googling the errors. I am sure you will find something.

yea, been trying, that, can't seem to find a resolution though, as I'm not really getting any error so to speak, the options just won't stay checked. Been looking for about a month for a fix on different forums and websites. oh well, i'm sure there will be a solution eventually. (ie maybe when the new plugins are no longer unsupported/unofficial)

---

### Post by damis648 on 2008-07-05
> **borlosky said:**
> yea, been trying, that, can't seem to find a resolution though, as I'm not really getting any error so to speak, the options just won't stay checked. Been looking for about a month for a fix on different forums and websites. oh well, i'm sure there will be a solution eventually. (ie maybe when the new plugins are no longer unsupported/unofficial)

Ah, I was referring to the compilation of the deformation plugin that was not working. As for your problem, they did compile correctly? The only reason I can come up with is that these plugins are not compatible with such a new version of compiz.

---

### Post by borlosky on 2008-07-05
> **damis648 said:**
> Ah, I was referring to the compilation of the deformation plugin that was not working. As for your problem, they did compile correctly? The only reason I can come up with is that these plugins are not compatible with such a new version of compiz.

actually the deformation plugin is the only one of the new plugins i can get to work. it's all the other new plugins that i'm having the trouble with. such as photowheel, stackswitch, snow globe, snow, screen saver, atlantis i can't enable. and I still have yet to see fireflies and leaves in my list of plugins. all the original plugins like 3d windows and water, fire, and such all work normally. as far as the version of compiz, i've tried on 7.5, 7.6 and 7.7, and the new plugins only appeear when i'm running 7.7. wasn't able to get to to even show in previous versions.

---

### Post by tjwoosta on 2008-07-06
( post removed )

---

### Post by stldirty on 2008-07-06
nvm...

---

### Post by borlosky on 2008-07-08
I was finally able to get all plugins working fine. Here's how I did it:

1: went to add/remove from Applications menu, removed all compiz related software

2: went to Synaptic package manager and COMPLETELY Removed ALL compiz related software

3: Followed steps located here: [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

4: Logged out, then back in. all working fine now!!:KS (all my previous keybindings were saved however, so very little configuration was needed other than just checking the new options)

::edit:: i also had to setup fusion icon to automatically load at start up to be able to use the new plugins

hope this helps

---

### Post by Newk1991 on 2008-07-10
borlesky, i had the same problem with compizconfig settings manager only allowing plugins to select plugins for a few seconds...

im presuming u didnt find a solution?

Newk

---

### Post by borlosky on 2008-07-10
> **Newk1991 said:**
> borlesky, i had the same problem with compizconfig settings manager only allowing plugins to select plugins for a few seconds...

im presuming u didnt find a solution?

Newk

actually i did find a solution, check my post directly above your post, i already put it in here :-)

---

### Post by cybugs on 2008-07-10
after reading page by page.. :) so? its won't work on compiz 0.7.6 ? coz i just install it yesterday .. thx

---

### Post by borlosky on 2008-07-10
> **cybugs said:**
> after reading page by page.. :) so? its won't work on compiz 0.7.6 ? coz i just install it yesterday .. thx

from what i understand it should work fine on 0.7.6. was able to also get plugins working on a separate ubuntu box running 0.7.4 as well.

---

### Post by MichaelLucky on 2008-07-10
hey im a new user, and I was wondering how to install this?

Edit: ok scratch that, apparently theres an instruction on page 2, thanks for the script!

---

### Post by Mr dirt on 2008-07-13
Just upgraded to 7.6 and the elements(i.e,fireflies) plugin will not stay checked for some reason, how can I keep it enabled. I like the sphere but I want the fireflies again.

---

### Post by chris4585 on 2008-07-13
I've read this thread, wondering should I risk messing up my compiz for one plugin.  I want the screensaver plugin, and as i saw no one had issues with it.  I have 8.04.1 with compiz 7.6, getting that plugin from get work properly with what i have?

also is this what i want since i only want the screensaver
```

sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core
cd
mkdir -p compiz
cd compiz
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
cd ..
chmod 777 compiz
cd compiz
cd screensaver
make
make install
cd ..
```

---

### Post by damis648 on 2008-07-13
> **chris4585 said:**
> I've read this thread, wondering should I risk messing up my compiz for one plugin.  I want the screensaver plugin, and as i saw no one had issues with it.  I have 8.04.1 with compiz 7.6, getting that plugin from get work properly with what i have?

also is this what i want since i only want the screensaver
```

sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core
cd
mkdir -p compiz
cd compiz
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
cd ..
chmod 777 compiz
cd compiz
cd screensaver
make
make install
cd ..
```

That should do it. :popcorn:

---

### Post by chris4585 on 2008-07-13
worked like a charm, thanks :D

Can i delete the compiz folder that the script made? ~/compiz

---

### Post by damis648 on 2008-07-14
> **chris4585 said:**
> worked like a charm, thanks :D

Can i delete the compiz folder that the script made? ~/compiz

Yes. It is just left there for recompiling if you update or uninstall or something.

---

### Post by chris4585 on 2008-07-14
ok thanks :)

---

### Post by okey666 on 2008-07-16
Fantastic script! Worked perfectly, it was taking me ages to install each extra plugin by its self.

---

### Post by damis648 on 2008-07-17
> **okey666 said:**
> Fantastic script! Worked perfectly, it was taking me ages to install each extra plugin by its self.

Glad it worked! :popcorn:

---

### Post by wantakill on 2008-07-23
Ok, I just installed ubuntu 8.04 yesterday and i'm a newbie to Linux. So I skimmed trough all the posts, i download the compiz-plugin, and I ticked some of the box in the window affect, but there is nothing happen. I try to make a cube desktop, and now i'm lost. :confused::confused: which boxes should I tick to make a cube desktop??? and can you give me the step by step instructions??  thx a lot

---

### Post by soctu on 2008-07-28
> **borlosky said:**
> I was finally able to get all plugins working fine. Here's how I did it:

1: went to add/remove from Applications menu, removed all compiz related software

2: went to Synaptic package manager and COMPLETELY Removed ALL compiz related software

3: Followed steps located here: [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

4: Logged out, then back in. all working fine now!!:KS (all my previous keybindings were saved however, so very little configuration was needed other than just checking the new options)

::edit:: i also had to setup fusion icon to automatically load at start up to be able to use the new plugins

hope this helps


Thanks for the link it worked (mostly) unfortunately Atlantis and the enviromentals do not work. Atlantis will not stay checked. I'm running Compiz 7.7:confused:

---

### Post by borlosky on 2008-07-29
You also have to make sure you're running the compiz-fuzion icon. that was the only way i was able to get the options to stay checked. (to auto run the compiz icon at start up, just go to System> Preferences> Sessions. Click "add", For name just type something like "Compiz" for command field type "fusion-icon" without the quotes. and type anything in comment. then restart, and compiz fusion icon will now start at first boot, and hopefully also allow you to enable the plugins. just make sure you load compiz-fusion settings manager from the icon)

---

### Post by soctu on 2008-07-29
> **borlosky said:**
> You also have to make sure you're running the compiz-fuzion icon. that was the only way i was able to get the options to stay checked. (to auto run the compiz icon at start up, just go to System> Preferences> Sessions. Click "add", For name just type something like "Compiz" for command field type "fusion-icon" without the quotes. and type anything in comment. then restart, and compiz fusion icon will now start at first boot, and hopefully also allow you to enable the plugins. just make sure you load compiz-fusion settings manager from the icon)

Interesting, I run the compiz icon from the programs menu under
system tools. That Icon was there after I installed compiz-git per the website instructions you posted. Now Compiz doesn't auto start from the boot, I have to manually click on the icon to get compiz working....well somewhat working...Any other ideas? :(

---

### Post by Gourgi on 2008-07-29
> **soctu said:**
> Interesting, I run the compiz icon from the programs menu under
system tools. That Icon was there after I installed compiz-git per the website instructions you posted. Now Compiz doesn't auto start from the boot, I have to manually click on the icon to get compiz working....well somewhat working...Any other ideas? :(

you could add fusion-icon to your sessions:
System -> Preferences -> Sessions  ,  click Add
use 
Name : whatever
command : fusion-icon -f 
Comment : whatever

i hope this does the trick 

i think there is a better solution by launching directly compiz through gconf but i can't find it know.. :(

---

### Post by jakspanna27 on 2008-07-29
I need a little assistance i've just downloaded and tryed to run in terminal and it says permission denied , and you have posted not to run this in root , what should i do , please help

---

### Post by soctu on 2008-07-31
> **Gourgi said:**
> you could add fusion-icon to your sessions:
System -> Preferences -> Sessions  ,  click Add
use 
Name : whatever
command : fusion-icon -f 
Comment : whatever

i hope this does the trick 

i think there is a better solution by launching directly compiz through gconf but i can't find it know.. :(

Okay I did just that, and now compiz comes up automatically,

Unfortunately, When I click on Atlantis 2, it still unmarks itself. Any ideas??:?::confused:

---

### Post by MedellinManDem on 2008-08-01
Is Compiz-Git something different than Compiz-Fusion? I have that running at the moment, the one with the cube etc.

---

### Post by Kileli on 2008-08-01
Anyone Have any idea why i would be getting this error?
> Initialized empty Git repository in /home/ty/compiz-plugins/cubeaddon/.git/
gitweb.beryl-project.org[0: 195.114.19.35]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
fetch-pack from 'git://gitweb.beryl-project.org/fusion/plugins/cubeaddon' failed.

Could it possibly be a network firewall issue?

---

### Post by Kileli on 2008-08-01
also when i use this command it asks for a password
> git-clone git+ssh://git.compiz-fusion.org/git/users/pafy/screensaver


---

### Post by MedellinManDem on 2008-08-01
> **MedellinManDem said:**
> Is Compiz-Git something different than Compiz-Fusion? I have that running at the moment, the one with the cube etc.

Anyone?

---

### Post by MedellinManDem on 2008-08-02
> **MedellinManDem said:**
> Is Compiz-Git something different than Compiz-Fusion? I have that running at the moment, the one with the cube etc.

Bump

---

### Post by Pablo Pablovski on 2008-08-03
> **MedellinManDem said:**
> Bump

No, they're the same thing. The git version contains the latest plugins, development code etc. Stuff there *can* occasionally be unstable for that reason, so you should be aware.

---

### Post by colobix on 2008-08-03
Thi is fantastic. great job sir,
Are thee any more plugins for compiz out there?
plz post links.

---

### Post by ruark1 on 2008-08-20
This worked perfectly until I followed this guide to get the sphere/cylinder effect. 
[http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28](http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28)

Can anyone shed some light on where the conflict might be?

---

### Post by soctu on 2008-08-20
> **soctu said:**
> Thanks for the link it worked (mostly) unfortunately Atlantis and the enviromentals do not work. Atlantis will not stay checked. I'm running Compiz 7.7:confused:

I still have these problems. I constantly update the plugins and still have the same results. I even tried unchecking everything and clicking only the needed plugins to run atlantis 2 or environmentals with the same results. Any ideas? Any known conflicts? Oddly enough I have the snow plugin that I can run independently of the environmentals and it works okay just like I can run gears and the photowheel inside the cube...but no fishies :-( :confused:](*,)](*,)

---

### Post by ruark1 on 2008-08-21
> **ruark1 said:**
> This worked perfectly until I followed this guide to get the sphere/cylinder effect. 
[http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28](http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28)

Can anyone shed some light on where the conflict might be?

Nevermind.
I reinstalled compiz, installed the cylinder plugin first then ran the script and it works great.
thank you very much.

---

### Post by Jhae on 2008-09-04
I have been trying to get the screensaver addon working for some time now, but when i get tothe point i have to 'make', it gives me an error.

convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : effect.cpp -> build/effect.lo
compiling : vector.cpp -> build/vector.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : wrapper.cpp -> build/wrapper.lo
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function 
‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for 
argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, 
const char*, ...)’
make: *** [build/screensaver.lo] Error 1


would anyone have some insight in to why this is happening?

---

### Post by ellalan on 2008-09-08
Thank you damis648, I have managed only the Cube Atlantis working and its wonderful. I am going to try the Screensaver(hopefuly I'll get it right).
I have one question about the CPU usage, while I use this plugin the CPU usage is 97% to 100%, could someone tell me what the consequences of this high CPU usage.TIA.

---

### Post by ellalan on 2008-09-08
Hi victormd
I have followed your instructions to install the screensaver and I get the message that screensaver is already installed but I couldn't see that plugin in CCSM.
I am running ubuntu Hardy Heron and I have got Cube Atlantis working, could you please tell me what I am missing here or do I have to start from scratch and install them one by one. I do really need these two plugins(Cube Atlantis and screensaver). Thank you for the help.

---

### Post by kfir on 2008-09-10
help please i got this eror :
> ompiling : snow.c -> build/snow.losnow.c: In function ‘updateSnowTextures’:
snow.c:459: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
snow.c:459: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
snow.c:459: error: incompatible type for argument 3 of ‘compLogMessage’
snow.c:463: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
snow.c:463: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
snow.c:463: error: incompatible type for argument 3 of ‘compLogMessage’
snow.c: In function ‘snowInitScreen’:
snow.c:545: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:545: error: too many arguments to function ‘compAddTimeout’
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:613: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:613: error: too many arguments to function ‘compAddTimeout’
make: *** [build/snow.lo] Error 1
compiling : snow.c -> build/snow.losnow.c: In function ‘updateSnowTextures’:
snow.c:459: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
snow.c:459: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
snow.c:459: error: incompatible type for argument 3 of ‘compLogMessage’
snow.c:463: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
snow.c:463: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
snow.c:463: error: incompatible type for argument 3 of ‘compLogMessage’
snow.c: In function ‘snowInitScreen’:
snow.c:545: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:545: error: too many arguments to function ‘compAddTimeout’
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:613: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:613: error: too many arguments to function ‘compAddTimeout’
make: *** [build/snow.lo] Error 1[QUOTE][/QUOTE]

any idea?

---

### Post by kfir on 2008-09-11
????

---

### Post by Twitch6000 on 2008-09-18
I am getting this error -

```

lies.c: In function ‘snowDisplayOptionChanged’:
fireflies.c:618: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:618: error: too many arguments to function ‘compAddTimeout’
make: *** [build/fireflies.lo] Error 1
compiling : fireflies.c -> build/fireflies.lofireflies.c: In function ‘updateSnowTextures’:
fireflies.c:475: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:475: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:475: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c:479: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:479: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:479: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c: In function ‘snowInitScreen’:
fireflies.c:551: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:551: error: too many arguments to function ‘compAddTimeout’
fireflies.c: In function ‘snowDisplayOptionChanged’:
fireflies.c:618: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:618: error: too many arguments to function ‘compAddTimeout’
make: *** [build/fireflies.lo] Error 1

```

On everything and that is just part of it.
How to fix it :(?

On PClinuxOS08 it makes everything easy by when you enable un supported packages you can install these things :/.

With ubuntu you have to get down and dirty lol.

---

### Post by errietta on 2008-09-25
it just wont work they disable themselves

---

### Post by brsmits on 2008-10-08
Strange, when I

./compizplugins.sh

it Gets the files fine, seems to unpack them with no problem, but then it begins doing:


Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Initialized empty Git repository in /home/smitz/compiz/anaglyph/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)
fetch-pack from 'git://anongit.compiz-fusion.org/users/wodor/anaglyph' failed.
Initialized empty Git repository in /home/smitz/compiz/atlantis2/.git/
.
.
.


with all the packages.  Any ideas?  I recently installed Hardy, is there a quick fix to this?

Ideas?

---

### Post by ruasoh on 2008-10-21
Has anyone been able to fix the problem with the atlantis box unchecking itself?  I have the same problem.   Everything else works fine, but when I check the atlantis box, it won't stay checked.

---

### Post by soctu on 2008-10-23
> **ruasoh said:**
> Has anyone been able to fix the problem with the atlantis box unchecking itself?  I have the same problem.   Everything else works fine, but when I check the atlantis box, it won't stay checked.


Thank You. I second the request. I've posted a few times
regarding the Atlantis issue with no success.
:popcorn:](*,)](*,)](*,)](*,)

---

### Post by jskiddy19 on 2008-10-23
What am I doing wrong here?

crab.c:70: warning: implicit declaration of function ‘glNormal3fv’
crab.c:70: warning: nested extern declaration of ‘glNormal3fv’
crab.c:71: warning: implicit declaration of function ‘glVertex3fv’
crab.c:71: warning: nested extern declaration of ‘glVertex3fv’
crab.c:353: warning: implicit declaration of function ‘glEnd’
crab.c:353: warning: nested extern declaration of ‘glEnd’
make: *** [build/crab.lo] Error 1
compiling : fireflies.c -> build/fireflies.lofireflies.c: In function ‘updateSnowTextures’:
fireflies.c:475: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:475: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:475: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c:479: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:479: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:479: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c: In function ‘snowInitScreen’:
fireflies.c:551: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:551: error: too many arguments to function ‘compAddTimeout’
fireflies.c: In function ‘snowDisplayOptionChanged’:
fireflies.c:618: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:618: error: too many arguments to function ‘compAddTimeout’
make: *** [build/fireflies.lo] Error 1
compiling : fireflies.c -> build/fireflies.lofireflies.c: In function ‘updateSnowTextures’:
fireflies.c:475: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:475: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:475: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c:479: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
fireflies.c:479: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
fireflies.c:479: error: incompatible type for argument 3 of ‘compLogMessage’
fireflies.c: In function ‘snowInitScreen’:
fireflies.c:551: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:551: error: too many arguments to function ‘compAddTimeout’
fireflies.c: In function ‘snowDisplayOptionChanged’:
fireflies.c:618: error: incompatible type for argument 2 of ‘compAddTimeout’
fireflies.c:618: error: too many arguments to function ‘compAddTimeout’
make: *** [build/fireflies.lo] Error 1
compiling : freewins.c -> build/freewins.lofreewins.c: In function ‘freewinsInitDisplay’:
freewins.c:346: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
freewins.c:346: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
freewins.c:346: error: incompatible type for argument 3 of ‘compLogMessage’
freewins.c:346: error: too few arguments to function ‘compLogMessage’
make: *** [build/freewins.lo] Error 1
compiling : freewins.c -> build/freewins.lofreewins.c: In function ‘freewinsInitDisplay’:
freewins.c:346: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
freewins.c:346: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
freewins.c:346: error: incompatible type for argument 3 of ‘compLogMessage’
freewins.c:346: error: too few arguments to function ‘compLogMessage’
make: *** [build/freewins.lo] Error 1
compiling : photo.c -> build/photo.lophoto.c: In function ‘photoTextureChange’:
photo.c:220: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
photo.c:220: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
photo.c:220: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/photo.lo] Error 1
compiling : photo.c -> build/photo.lophoto.c: In function ‘photoTextureChange’:
photo.c:220: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
photo.c:220: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
photo.c:220: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/photo.lo] Error 1
compiling : rotatingcube.cpp -> build/rotatingcube.lorm: cannot remove `build/rotatingcube.loT': Permission denied
rm: cannot remove `build/rotatingcube.loT': Permission denied
/usr/bin/libtool: line 1283: build/rotatingcube.loT: Permission denied
In file included from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
screensaver_internal.h:5:18: error: cube.h: No such file or directory
In file included from matrix.h:6,
                 from screensaver_internal.h:7,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
vector.h: In member function ‘Vector Vector::toScreenSpace(CompScreen*) const’:
vector.h:37: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:38: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h: In member function ‘Vector Vector::toCoordsSpace(CompScreen*) const’:
vector.h:46: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:47: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
In file included from screensaver_internal.h:7,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
matrix.h: At global scope:
matrix.h:15: error: expected ‘,’ or ‘...’ before ‘*’ token
matrix.h:15: error: ISO C++ forbids declaration of ‘CompTransform’ with no type
matrix.h: In constructor ‘Matrix::Matrix(int)’:
matrix.h:15: error: ‘mat’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::rotate(float, float, float, float)’:
matrix.h:30: error: ‘CompTransform’ was not declared in this scope
matrix.h:30: error: expected primary-expression before ‘)’ token
matrix.h:30: error: ‘matrixRotate’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::scale(float, float, float)’:
matrix.h:38: error: ‘CompTransform’ was not declared in this scope
matrix.h:38: error: expected primary-expression before ‘)’ token
matrix.h:38: error: ‘matrixScale’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::translate(float, float, float)’:
matrix.h:46: error: ‘CompTransform’ was not declared in this scope
matrix.h:46: error: expected primary-expression before ‘)’ token
matrix.h:46: error: ‘matrixTranslate’ was not declared in this scope
In file included from screensaver_internal.h:9,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
build/screensaver_options.h: At global scope:
build/screensaver_options.h:19: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:58: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:59: error: ‘CompActionCallBackProc’ has not been declared
build/screensaver_options.h:60: error: ‘CompActionCallBackProc’ has not been declared
build/screensaver_options.h:68: error: ‘Bool’ does not name a type
build/screensaver_options.h:84: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:88: error: ‘Bool’ does not name a type
build/screensaver_options.h:100: error: ‘Bool’ does not name a type
In file included from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
screensaver_internal.h:45: error: ‘Bool’ does not name a type
screensaver_internal.h:46: error: ‘Bool’ does not name a type
screensaver_internal.h:47: error: ‘Bool’ does not name a type
screensaver_internal.h:53: error: ‘Bool’ does not name a type
screensaver_internal.h:62: error: ‘HandleEventProc’ does not name a type
screensaver_internal.h:72: error: ‘CubeGetRotationProc’ does not name a type
screensaver_internal.h:73: error: ‘PreparePaintScreenProc’ does not name a type
screensaver_internal.h:74: error: ‘DonePaintScreenProc’ does not name a type
screensaver_internal.h:75: error: ‘PaintOutputProc’ does not name a type
screensaver_internal.h:76: error: ‘PaintWindowProc’ does not name a type
screensaver_internal.h:77: error: ‘PaintTransformedOutputProc’ does not name a type
screensaver_internal.h:78: error: ‘PaintBackgroundProc’ does not name a type
screensaver_internal.h:94: error: ‘GLushort’ does not name a type
screensaver_internal.h:102: error: ‘XEvent’ has not been declared
screensaver_internal.h:106: error: expected ‘,’ or ‘...’ before ‘*’ token
screensaver_internal.h:106: error: ISO C++ forbids declaration of ‘ScreenPaintAttrib’ with no type
screensaver_internal.h:110: error: ‘Bool’ does not name a type
screensaver_internal.h:114: error: ‘Bool’ does not name a type
screensaver_internal.h:117: error: ‘Region’ has not been declared
In file included from screensaver_internal.h:119,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
wrapper.h:12: error: ‘XEvent’ has not been declared
wrapper.h:28: error: expected ‘,’ or ‘...’ before ‘*’ token
wrapper.h:28: error: ISO C++ forbids declaration of ‘ScreenPaintAttrib’ with no type
wrapper.h:31: error: ‘Bool’ does not name a type
wrapper.h:34: error: ‘Region’ has not been declared
wrapper.h:46: error: ‘Bool’ does not name a type
In file included from rotatingcube.cpp:1:
rotatingcube.h:17: error: ‘Bool’ does not name a type
rotatingcube.cpp: In member function ‘bool ScreenRotatingCube::loadCubePlugin()’:
rotatingcube.cpp:5: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:6: error: ‘findActivePlugin’ was not declared in this scope
rotatingcube.cpp:11: error: invalid use of incomplete type ‘struct _CompPlugin’
/usr/include/compiz/compiz.h:46: error: forward declaration of ‘struct _CompPlugin’
rotatingcube.cpp:14: error: invalid use of incomplete type ‘struct _CompPlugin’
/usr/include/compiz/compiz.h:46: error: forward declaration of ‘struct _CompPlugin’
rotatingcube.cpp:16: error: ‘getIntOptionNamed’ was not declared in this scope
rotatingcube.cpp:16: error: ‘CUBE_ABIVERSION’ was not declared in this scope
rotatingcube.cpp:18: error: ‘CompLogLevelError’ was not declared in this scope
rotatingcube.cpp:19: error: ‘compLogMessage’ was not declared in this scope
rotatingcube.cpp:23: error: ‘getIntOptionNamed’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual bool ScreenRotatingCube::enable()’:
rotatingcube.cpp:32: error: ‘CUBE_SCREEN’ was not declared in this scope
rotatingcube.cpp:37: error: ‘cs’ was not declared in this scope
rotatingcube.cpp:37: error: ‘RotationManual’ was not declared in this scope
rotatingcube.cpp:38: error: ‘WRAP’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::clean()’:
rotatingcube.cpp:54: error: ‘CUBE_SCREEN’ was not declared in this scope
rotatingcube.cpp:55: error: ‘cs’ was not declared in this scope
rotatingcube.cpp:55: error: ‘RotationNone’ was not declared in this scope
rotatingcube.cpp:56: error: ‘UNWRAP’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::preparePaintScreen(int)’:
rotatingcube.cpp:72: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:75: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:77: error: ‘struct ScreenSaverState’ has no member named ‘fadingIn’
rotatingcube.cpp:80: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:82: error: ‘struct ScreenSaverState’ has no member named ‘fadingOut’
rotatingcube.cpp:89: error: ‘struct ScreenSaverState’ has no member named ‘fadingOut’
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::donePaintScreen()’:
rotatingcube.cpp:100: error: ‘damageScreen’ was not declared in this scope
rotatingcube.cpp: At global scope:
rotatingcube.cpp:104: error: ‘Bool’ does not name a type
make: *** [build/rotatingcube.lo] Error 1
compiling : rotatingcube.cpp -> build/rotatingcube.lorm: cannot remove `build/rotatingcube.loT': Permission denied
rm: cannot remove `build/rotatingcube.loT': Permission denied
/usr/bin/libtool: line 1283: build/rotatingcube.loT: Permission denied
In file included from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
screensaver_internal.h:5:18: error: cube.h: No such file or directory
In file included from matrix.h:6,
                 from screensaver_internal.h:7,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
vector.h: In member function ‘Vector Vector::toScreenSpace(CompScreen*) const’:
vector.h:37: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:38: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h: In member function ‘Vector Vector::toCoordsSpace(CompScreen*) const’:
vector.h:46: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:47: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
In file included from screensaver_internal.h:7,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
matrix.h: At global scope:
matrix.h:15: error: expected ‘,’ or ‘...’ before ‘*’ token
matrix.h:15: error: ISO C++ forbids declaration of ‘CompTransform’ with no type
matrix.h: In constructor ‘Matrix::Matrix(int)’:
matrix.h:15: error: ‘mat’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::rotate(float, float, float, float)’:
matrix.h:30: error: ‘CompTransform’ was not declared in this scope
matrix.h:30: error: expected primary-expression before ‘)’ token
matrix.h:30: error: ‘matrixRotate’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::scale(float, float, float)’:
matrix.h:38: error: ‘CompTransform’ was not declared in this scope
matrix.h:38: error: expected primary-expression before ‘)’ token
matrix.h:38: error: ‘matrixScale’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::translate(float, float, float)’:
matrix.h:46: error: ‘CompTransform’ was not declared in this scope
matrix.h:46: error: expected primary-expression before ‘)’ token
matrix.h:46: error: ‘matrixTranslate’ was not declared in this scope
In file included from screensaver_internal.h:9,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
build/screensaver_options.h: At global scope:
build/screensaver_options.h:19: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:58: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:59: error: ‘CompActionCallBackProc’ has not been declared
build/screensaver_options.h:60: error: ‘CompActionCallBackProc’ has not been declared
build/screensaver_options.h:68: error: ‘Bool’ does not name a type
build/screensaver_options.h:84: error: expected constructor, destructor, or type conversion before ‘*’ token
build/screensaver_options.h:88: error: ‘Bool’ does not name a type
build/screensaver_options.h:100: error: ‘Bool’ does not name a type
In file included from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
screensaver_internal.h:45: error: ‘Bool’ does not name a type
screensaver_internal.h:46: error: ‘Bool’ does not name a type
screensaver_internal.h:47: error: ‘Bool’ does not name a type
screensaver_internal.h:53: error: ‘Bool’ does not name a type
screensaver_internal.h:62: error: ‘HandleEventProc’ does not name a type
screensaver_internal.h:72: error: ‘CubeGetRotationProc’ does not name a type
screensaver_internal.h:73: error: ‘PreparePaintScreenProc’ does not name a type
screensaver_internal.h:74: error: ‘DonePaintScreenProc’ does not name a type
screensaver_internal.h:75: error: ‘PaintOutputProc’ does not name a type
screensaver_internal.h:76: error: ‘PaintWindowProc’ does not name a type
screensaver_internal.h:77: error: ‘PaintTransformedOutputProc’ does not name a type
screensaver_internal.h:78: error: ‘PaintBackgroundProc’ does not name a type
screensaver_internal.h:94: error: ‘GLushort’ does not name a type
screensaver_internal.h:102: error: ‘XEvent’ has not been declared
screensaver_internal.h:106: error: expected ‘,’ or ‘...’ before ‘*’ token
screensaver_internal.h:106: error: ISO C++ forbids declaration of ‘ScreenPaintAttrib’ with no type
screensaver_internal.h:110: error: ‘Bool’ does not name a type
screensaver_internal.h:114: error: ‘Bool’ does not name a type
screensaver_internal.h:117: error: ‘Region’ has not been declared
In file included from screensaver_internal.h:119,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
wrapper.h:12: error: ‘XEvent’ has not been declared
wrapper.h:28: error: expected ‘,’ or ‘...’ before ‘*’ token
wrapper.h:28: error: ISO C++ forbids declaration of ‘ScreenPaintAttrib’ with no type
wrapper.h:31: error: ‘Bool’ does not name a type
wrapper.h:34: error: ‘Region’ has not been declared
wrapper.h:46: error: ‘Bool’ does not name a type
In file included from rotatingcube.cpp:1:
rotatingcube.h:17: error: ‘Bool’ does not name a type
rotatingcube.cpp: In member function ‘bool ScreenRotatingCube::loadCubePlugin()’:
rotatingcube.cpp:5: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:6: error: ‘findActivePlugin’ was not declared in this scope
rotatingcube.cpp:11: error: invalid use of incomplete type ‘struct _CompPlugin’
/usr/include/compiz/compiz.h:46: error: forward declaration of ‘struct _CompPlugin’
rotatingcube.cpp:14: error: invalid use of incomplete type ‘struct _CompPlugin’
/usr/include/compiz/compiz.h:46: error: forward declaration of ‘struct _CompPlugin’
rotatingcube.cpp:16: error: ‘getIntOptionNamed’ was not declared in this scope
rotatingcube.cpp:16: error: ‘CUBE_ABIVERSION’ was not declared in this scope
rotatingcube.cpp:18: error: ‘CompLogLevelError’ was not declared in this scope
rotatingcube.cpp:19: error: ‘compLogMessage’ was not declared in this scope
rotatingcube.cpp:23: error: ‘getIntOptionNamed’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual bool ScreenRotatingCube::enable()’:
rotatingcube.cpp:32: error: ‘CUBE_SCREEN’ was not declared in this scope
rotatingcube.cpp:37: error: ‘cs’ was not declared in this scope
rotatingcube.cpp:37: error: ‘RotationManual’ was not declared in this scope
rotatingcube.cpp:38: error: ‘WRAP’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::clean()’:
rotatingcube.cpp:54: error: ‘CUBE_SCREEN’ was not declared in this scope
rotatingcube.cpp:55: error: ‘cs’ was not declared in this scope
rotatingcube.cpp:55: error: ‘RotationNone’ was not declared in this scope
rotatingcube.cpp:56: error: ‘UNWRAP’ was not declared in this scope
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::preparePaintScreen(int)’:
rotatingcube.cpp:72: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:75: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:77: error: ‘struct ScreenSaverState’ has no member named ‘fadingIn’
rotatingcube.cpp:80: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
rotatingcube.cpp:82: error: ‘struct ScreenSaverState’ has no member named ‘fadingOut’
rotatingcube.cpp:89: error: ‘struct ScreenSaverState’ has no member named ‘fadingOut’
rotatingcube.cpp: In member function ‘virtual void ScreenRotatingCube::donePaintScreen()’:
rotatingcube.cpp:100: error: ‘damageScreen’ was not declared in this scope
rotatingcube.cpp: At global scope:
rotatingcube.cpp:104: error: ‘Bool’ does not name a type
make: *** [build/rotatingcube.lo] Error 1
compiling : snow.c -> build/snow.loIn file included from snow.c:39:
build/snow_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:109: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/snow_options.h:110: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
snow.c:68: error: expected specifier-qualifier-list before ‘CompTexture’
snow.c:95: error: expected specifier-qualifier-list before ‘PaintOutputProc’
snow.c: In function ‘snowThink’:
snow.c:117: error: dereferencing pointer to incomplete type
snow.c:119: error: dereferencing pointer to incomplete type
snow.c:121: error: dereferencing pointer to incomplete type
snow.c:122: error: dereferencing pointer to incomplete type
snow.c:127: error: dereferencing pointer to incomplete type
snow.c: In function ‘stepSnowPositions’:
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:154: error: ‘TRUE’ undeclared (first use in this function)
snow.c:154: error: (Each undeclared identifier is reported only once
snow.c:154: error: for each function it appears in.)
snow.c:156: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:157: error: dereferencing pointer to incomplete type
snow.c:158: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:169: error: dereferencing pointer to incomplete type
snow.c:169: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
snow.c:170: warning: implicit declaration of function ‘addWindowDamage’
snow.c:170: warning: nested extern declaration of ‘addWindowDamage’
snow.c:174: warning: implicit declaration of function ‘damageScreen’
snow.c:174: warning: nested extern declaration of ‘damageScreen’
snow.c:177: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:181: error: expected declaration specifiers or ‘...’ before ‘CompAction’
snow.c:182: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
snow.c: In function ‘snowToggle’:
snow.c:189: warning: implicit declaration of function ‘getIntOptionNamed’
snow.c:189: warning: nested extern declaration of ‘getIntOptionNamed’
snow.c:190: warning: implicit declaration of function ‘findScreenAtDisplay’
snow.c:190: warning: nested extern declaration of ‘findScreenAtDisplay’
snow.c:190: warning: assignment makes pointer from integer without a cast
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:200: error: ‘TRUE’ undeclared (first use in this function)
snow.c:201: warning: control reaches end of non-void function
snow.c: In function ‘setupDisplayList’:
snow.c:224: error: dereferencing pointer to incomplete type
snow.c:226: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:226: warning: implicit declaration of function ‘glGenLists’
snow.c:226: warning: nested extern declaration of ‘glGenLists’
snow.c:228: warning: implicit declaration of function ‘glNewList’
snow.c:228: warning: nested extern declaration of ‘glNewList’
snow.c:228: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:228: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:229: warning: implicit declaration of function ‘glBegin’
snow.c:229: warning: nested extern declaration of ‘glBegin’
snow.c:229: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:231: warning: implicit declaration of function ‘glColor4f’
snow.c:231: warning: nested extern declaration of ‘glColor4f’
snow.c:232: warning: implicit declaration of function ‘glVertex3f’
snow.c:232: warning: nested extern declaration of ‘glVertex3f’
snow.c:240: warning: implicit declaration of function ‘glEnd’
snow.c:240: warning: nested extern declaration of ‘glEnd’
snow.c:241: warning: implicit declaration of function ‘glEndList’
snow.c:241: warning: nested extern declaration of ‘glEndList’
snow.c: In function ‘beginRendering’:
snow.c:248: error: dereferencing pointer to incomplete type
snow.c:249: warning: implicit declaration of function ‘glEnable’
snow.c:249: warning: nested extern declaration of ‘glEnable’
snow.c:249: error: ‘GL_BLEND’ undeclared (first use in this function)
snow.c:251: warning: implicit declaration of function ‘glTexEnvf’
snow.c:251: warning: nested extern declaration of ‘glTexEnvf’
snow.c:251: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
snow.c:251: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
snow.c:251: error: ‘GL_MODULATE’ undeclared (first use in this function)
snow.c:253: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘FALSE’ undeclared (first use in this function)
snow.c:260: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:260: error: dereferencing pointer to incomplete type
snow.c:264: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:266: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:267: error: dereferencing pointer to incomplete type
snow.c:268: error: dereferencing pointer to incomplete type
snow.c:270: warning: implicit declaration of function ‘enableTexture’
snow.c:270: warning: nested extern declaration of ‘enableTexture’
snow.c:270: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:271: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
snow.c:275: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:277: warning: implicit declaration of function ‘glTranslatef’
snow.c:277: warning: nested extern declaration of ‘glTranslatef’
snow.c:279: warning: implicit declaration of function ‘glRotatef’
snow.c:279: warning: nested extern declaration of ‘glRotatef’
snow.c:280: warning: implicit declaration of function ‘glCallList’
snow.c:280: warning: nested extern declaration of ‘glCallList’
snow.c:280: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:287: warning: implicit declaration of function ‘disableTexture’
snow.c:287: warning: nested extern declaration of ‘disableTexture’
snow.c:287: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:292: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:293: error: dereferencing pointer to incomplete type
snow.c:299: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:306: error: ‘GL_REPLACE’ undeclared (first use in this function)
snow.c:307: error: dereferencing pointer to incomplete type
snow.c:309: warning: implicit declaration of function ‘glDisable’
snow.c:309: warning: nested extern declaration of ‘glDisable’
snow.c:310: warning: implicit declaration of function ‘glBlendFunc’
snow.c:310: warning: nested extern declaration of ‘glBlendFunc’
snow.c:310: error: ‘GL_ONE’ undeclared (first use in this function)
snow.c:310: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
snow.c: At top level:
snow.c:318: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
snow.c:318: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c:352: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
snow.c:352: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c: In function ‘initiateSnowFlake’:
snow.c:381: error: dereferencing pointer to incomplete type
snow.c:383: error: dereferencing pointer to incomplete type
snow.c:386: error: dereferencing pointer to incomplete type
snow.c:392: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:400: error: dereferencing pointer to incomplete type
snow.c:406: error: dereferencing pointer to incomplete type
snow.c:413: error: dereferencing pointer to incomplete type
snow.c: In function ‘setSnowflakeTexture’:
snow.c:423: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c: In function ‘updateSnowTextures’:
snow.c:431: error: dereferencing pointer to incomplete type
snow.c:432: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:436: error: dereferencing pointer to incomplete type
snow.c:438: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:440: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:442: warning: implicit declaration of function ‘finiTexture’
snow.c:442: warning: nested extern declaration of ‘finiTexture’
snow.c:442: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:443: warning: implicit declaration of function ‘glDeleteLists’
snow.c:443: warning: nested extern declaration of ‘glDeleteLists’
snow.c:443: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:446: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:447: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:448: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:450: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:454: error: ‘CompMatrix’ undeclared (first use in this function)
snow.c:454: error: ‘mat’ undeclared (first use in this function)
snow.c:457: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:458: warning: implicit declaration of function ‘readImageToTexture’
snow.c:458: warning: nested extern declaration of ‘readImageToTexture’
snow.c:458: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:459: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:459: error: dereferencing pointer to incomplete type
snow.c:460: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:461: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:462: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:464: warning: implicit declaration of function ‘compLogMessage’
snow.c:464: warning: nested extern declaration of ‘compLogMessage’
snow.c:464: error: dereferencing pointer to incomplete type
snow.c:464: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
snow.c:465: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:465: error: dereferencing pointer to incomplete type
snow.c:468: error: dereferencing pointer to incomplete type
snow.c:468: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
snow.c:469: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:469: error: dereferencing pointer to incomplete type
snow.c:471: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:472: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:474: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:477: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:479: warning: implicit declaration of function ‘glTexCoord2f’
snow.c:479: warning: nested extern declaration of ‘glTexCoord2f’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
snow.c:480: warning: implicit declaration of function ‘glVertex2f’
snow.c:480: warning: nested extern declaration of ‘glVertex2f’
snow.c:482: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘width’
snow.c:484: error: ‘SnowTexture’ has no member named ‘width’
snow.c:485: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘width’
snow.c:487: error: ‘SnowTexture’ has no member named ‘width’
snow.c:497: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c: In function ‘snowInitScreen’:
snow.c:510: error: dereferencing pointer to incomplete type
snow.c:513: error: dereferencing pointer to incomplete type
snow.c:517: error: dereferencing pointer to incomplete type
snow.c:520: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:521: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:522: error: ‘FALSE’ undeclared (first use in this function)
snow.c:523: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:525: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:537: warning: implicit declaration of function ‘WRAP’
snow.c:537: warning: nested extern declaration of ‘WRAP’
snow.c:537: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:537: error: ‘snowPaintOutput’ undeclared (first use in this function)
snow.c:538: error: ‘drawWindow’ undeclared (first use in this function)
snow.c:538: error: ‘snowDrawWindow’ undeclared (first use in this function)
snow.c:540: error: dereferencing pointer to incomplete type
snow.c:543: error: ‘TRUE’ undeclared (first use in this function)
snow.c:544: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniScreen’:
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:557: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:559: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:560: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:563: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:564: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:566: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:567: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:569: warning: implicit declaration of function ‘UNWRAP’
snow.c:569: warning: nested extern declaration of ‘UNWRAP’
snow.c:569: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:570: error: ‘drawWindow’ undeclared (first use in this function)
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:580: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:591: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:591: error: ‘TRUE’ undeclared (first use in this function)
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:624: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:642: error: dereferencing pointer to incomplete type
snow.c:643: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c: In function ‘snowInitDisplay’:
snow.c:663: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
snow.c:663: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
snow.c:667: error: ‘FALSE’ undeclared (first use in this function)
snow.c:670: error: too many arguments to function ‘snowSetToggleInitiate’
snow.c:677: error: dereferencing pointer to incomplete type
snow.c:678: error: dereferencing pointer to incomplete type
snow.c:680: error: dereferencing pointer to incomplete type
snow.c:682: error: ‘TRUE’ undeclared (first use in this function)
snow.c:683: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniDisplay’:
snow.c:689: error: dereferencing pointer to incomplete type
snow.c:691: warning: implicit declaration of function ‘freeScreenPrivateIndex’
snow.c:691: warning: nested extern declaration of ‘freeScreenPrivateIndex’
snow.c: In function ‘snowInit’:
snow.c:698: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
snow.c:698: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
snow.c:700: error: ‘FALSE’ undeclared (first use in this function)
snow.c:702: error: ‘TRUE’ undeclared (first use in this function)
snow.c:703: warning: control reaches end of non-void function
snow.c: In function ‘snowFini’:
snow.c:708: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
snow.c:708: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
snow.c: In function ‘snowGetVersion’:
snow.c:715: error: ‘ABIVERSION’ undeclared (first use in this function)
snow.c:716: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:718: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snowVTable’
snow.c:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/snow.lo] Error 1
compiling : snow.c -> build/snow.loIn file included from snow.c:39:
build/snow_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:109: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/snow_options.h:110: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
snow.c:68: error: expected specifier-qualifier-list before ‘CompTexture’
snow.c:95: error: expected specifier-qualifier-list before ‘PaintOutputProc’
snow.c: In function ‘snowThink’:
snow.c:117: error: dereferencing pointer to incomplete type
snow.c:119: error: dereferencing pointer to incomplete type
snow.c:121: error: dereferencing pointer to incomplete type
snow.c:122: error: dereferencing pointer to incomplete type
snow.c:127: error: dereferencing pointer to incomplete type
snow.c: In function ‘stepSnowPositions’:
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:154: error: ‘TRUE’ undeclared (first use in this function)
snow.c:154: error: (Each undeclared identifier is reported only once
snow.c:154: error: for each function it appears in.)
snow.c:156: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:157: error: dereferencing pointer to incomplete type
snow.c:158: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:169: error: dereferencing pointer to incomplete type
snow.c:169: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
snow.c:170: warning: implicit declaration of function ‘addWindowDamage’
snow.c:170: warning: nested extern declaration of ‘addWindowDamage’
snow.c:174: warning: implicit declaration of function ‘damageScreen’
snow.c:174: warning: nested extern declaration of ‘damageScreen’
snow.c:177: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:181: error: expected declaration specifiers or ‘...’ before ‘CompAction’
snow.c:182: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
snow.c: In function ‘snowToggle’:
snow.c:189: warning: implicit declaration of function ‘getIntOptionNamed’
snow.c:189: warning: nested extern declaration of ‘getIntOptionNamed’
snow.c:190: warning: implicit declaration of function ‘findScreenAtDisplay’
snow.c:190: warning: nested extern declaration of ‘findScreenAtDisplay’
snow.c:190: warning: assignment makes pointer from integer without a cast
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:200: error: ‘TRUE’ undeclared (first use in this function)
snow.c:201: warning: control reaches end of non-void function
snow.c: In function ‘setupDisplayList’:
snow.c:224: error: dereferencing pointer to incomplete type
snow.c:226: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:226: warning: implicit declaration of function ‘glGenLists’
snow.c:226: warning: nested extern declaration of ‘glGenLists’
snow.c:228: warning: implicit declaration of function ‘glNewList’
snow.c:228: warning: nested extern declaration of ‘glNewList’
snow.c:228: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:228: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:229: warning: implicit declaration of function ‘glBegin’
snow.c:229: warning: nested extern declaration of ‘glBegin’
snow.c:229: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:231: warning: implicit declaration of function ‘glColor4f’
snow.c:231: warning: nested extern declaration of ‘glColor4f’
snow.c:232: warning: implicit declaration of function ‘glVertex3f’
snow.c:232: warning: nested extern declaration of ‘glVertex3f’
snow.c:240: warning: implicit declaration of function ‘glEnd’
snow.c:240: warning: nested extern declaration of ‘glEnd’
snow.c:241: warning: implicit declaration of function ‘glEndList’
snow.c:241: warning: nested extern declaration of ‘glEndList’
snow.c: In function ‘beginRendering’:
snow.c:248: error: dereferencing pointer to incomplete type
snow.c:249: warning: implicit declaration of function ‘glEnable’
snow.c:249: warning: nested extern declaration of ‘glEnable’
snow.c:249: error: ‘GL_BLEND’ undeclared (first use in this function)
snow.c:251: warning: implicit declaration of function ‘glTexEnvf’
snow.c:251: warning: nested extern declaration of ‘glTexEnvf’
snow.c:251: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
snow.c:251: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
snow.c:251: error: ‘GL_MODULATE’ undeclared (first use in this function)
snow.c:253: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘FALSE’ undeclared (first use in this function)
snow.c:260: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:260: error: dereferencing pointer to incomplete type
snow.c:264: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:266: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:267: error: dereferencing pointer to incomplete type
snow.c:268: error: dereferencing pointer to incomplete type
snow.c:270: warning: implicit declaration of function ‘enableTexture’
snow.c:270: warning: nested extern declaration of ‘enableTexture’
snow.c:270: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:271: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
snow.c:275: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:277: warning: implicit declaration of function ‘glTranslatef’
snow.c:277: warning: nested extern declaration of ‘glTranslatef’
snow.c:279: warning: implicit declaration of function ‘glRotatef’
snow.c:279: warning: nested extern declaration of ‘glRotatef’
snow.c:280: warning: implicit declaration of function ‘glCallList’
snow.c:280: warning: nested extern declaration of ‘glCallList’
snow.c:280: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:287: warning: implicit declaration of function ‘disableTexture’
snow.c:287: warning: nested extern declaration of ‘disableTexture’
snow.c:287: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:292: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:293: error: dereferencing pointer to incomplete type
snow.c:299: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:306: error: ‘GL_REPLACE’ undeclared (first use in this function)
snow.c:307: error: dereferencing pointer to incomplete type
snow.c:309: warning: implicit declaration of function ‘glDisable’
snow.c:309: warning: nested extern declaration of ‘glDisable’
snow.c:310: warning: implicit declaration of function ‘glBlendFunc’
snow.c:310: warning: nested extern declaration of ‘glBlendFunc’
snow.c:310: error: ‘GL_ONE’ undeclared (first use in this function)
snow.c:310: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
snow.c: At top level:
snow.c:318: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
snow.c:318: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c:352: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
snow.c:352: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c: In function ‘initiateSnowFlake’:
snow.c:381: error: dereferencing pointer to incomplete type
snow.c:383: error: dereferencing pointer to incomplete type
snow.c:386: error: dereferencing pointer to incomplete type
snow.c:392: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:400: error: dereferencing pointer to incomplete type
snow.c:406: error: dereferencing pointer to incomplete type
snow.c:413: error: dereferencing pointer to incomplete type
snow.c: In function ‘setSnowflakeTexture’:
snow.c:423: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c: In function ‘updateSnowTextures’:
snow.c:431: error: dereferencing pointer to incomplete type
snow.c:432: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:436: error: dereferencing pointer to incomplete type
snow.c:438: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:440: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:442: warning: implicit declaration of function ‘finiTexture’
snow.c:442: warning: nested extern declaration of ‘finiTexture’
snow.c:442: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:443: warning: implicit declaration of function ‘glDeleteLists’
snow.c:443: warning: nested extern declaration of ‘glDeleteLists’
snow.c:443: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:446: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:447: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:448: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:450: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:454: error: ‘CompMatrix’ undeclared (first use in this function)
snow.c:454: error: ‘mat’ undeclared (first use in this function)
snow.c:457: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:458: warning: implicit declaration of function ‘readImageToTexture’
snow.c:458: warning: nested extern declaration of ‘readImageToTexture’
snow.c:458: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:459: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:459: error: dereferencing pointer to incomplete type
snow.c:460: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:461: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:462: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:464: warning: implicit declaration of function ‘compLogMessage’
snow.c:464: warning: nested extern declaration of ‘compLogMessage’
snow.c:464: error: dereferencing pointer to incomplete type
snow.c:464: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
snow.c:465: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:465: error: dereferencing pointer to incomplete type
snow.c:468: error: dereferencing pointer to incomplete type
snow.c:468: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
snow.c:469: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:469: error: dereferencing pointer to incomplete type
snow.c:471: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:472: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:474: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:477: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:479: warning: implicit declaration of function ‘glTexCoord2f’
snow.c:479: warning: nested extern declaration of ‘glTexCoord2f’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
snow.c:480: warning: implicit declaration of function ‘glVertex2f’
snow.c:480: warning: nested extern declaration of ‘glVertex2f’
snow.c:482: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘width’
snow.c:484: error: ‘SnowTexture’ has no member named ‘width’
snow.c:485: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘width’
snow.c:487: error: ‘SnowTexture’ has no member named ‘width’
snow.c:497: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c: In function ‘snowInitScreen’:
snow.c:510: error: dereferencing pointer to incomplete type
snow.c:513: error: dereferencing pointer to incomplete type
snow.c:517: error: dereferencing pointer to incomplete type
snow.c:520: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:521: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:522: error: ‘FALSE’ undeclared (first use in this function)
snow.c:523: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:525: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:537: warning: implicit declaration of function ‘WRAP’
snow.c:537: warning: nested extern declaration of ‘WRAP’
snow.c:537: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:537: error: ‘snowPaintOutput’ undeclared (first use in this function)
snow.c:538: error: ‘drawWindow’ undeclared (first use in this function)
snow.c:538: error: ‘snowDrawWindow’ undeclared (first use in this function)
snow.c:540: error: dereferencing pointer to incomplete type
snow.c:543: error: ‘TRUE’ undeclared (first use in this function)
snow.c:544: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniScreen’:
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:557: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:559: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:560: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:563: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:564: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:566: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:567: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:569: warning: implicit declaration of function ‘UNWRAP’
snow.c:569: warning: nested extern declaration of ‘UNWRAP’
snow.c:569: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:570: error: ‘drawWindow’ undeclared (first use in this function)
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:580: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:591: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:591: error: ‘TRUE’ undeclared (first use in this function)
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:624: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:642: error: dereferencing pointer to incomplete type
snow.c:643: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c: In function ‘snowInitDisplay’:
snow.c:663: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
snow.c:663: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
snow.c:667: error: ‘FALSE’ undeclared (first use in this function)
snow.c:670: error: too many arguments to function ‘snowSetToggleInitiate’
snow.c:677: error: dereferencing pointer to incomplete type
snow.c:678: error: dereferencing pointer to incomplete type
snow.c:680: error: dereferencing pointer to incomplete type
snow.c:682: error: ‘TRUE’ undeclared (first use in this function)
snow.c:683: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniDisplay’:
snow.c:689: error: dereferencing pointer to incomplete type
snow.c:691: warning: implicit declaration of function ‘freeScreenPrivateIndex’
snow.c:691: warning: nested extern declaration of ‘freeScreenPrivateIndex’
snow.c: In function ‘snowInit’:
snow.c:698: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
snow.c:698: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
snow.c:700: error: ‘FALSE’ undeclared (first use in this function)
snow.c:702: error: ‘TRUE’ undeclared (first use in this function)
snow.c:703: warning: control reaches end of non-void function
snow.c: In function ‘snowFini’:
snow.c:708: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
snow.c:708: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
snow.c: In function ‘snowGetVersion’:
snow.c:715: error: ‘ABIVERSION’ undeclared (first use in this function)
snow.c:716: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:718: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snowVTable’
snow.c:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/snow.lo] Error 1
install   : /home/jason/.compiz/plugins/libsnowglobe.soinstall: cannot create regular file `/home/jason/.compiz/plugins/libsnowglobe.so': Permission denied
make: *** [install] Error 1
compiling : star.c -> build/star.lostar.c: In function ‘updateSnowTextures’:
star.c:513: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
star.c:513: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
star.c:513: error: incompatible type for argument 3 of ‘compLogMessage’
star.c:517: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
star.c:517: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
star.c:517: error: incompatible type for argument 3 of ‘compLogMessage’
star.c: In function ‘snowInitScreen’:
star.c:589: error: incompatible type for argument 2 of ‘compAddTimeout’
star.c:589: error: too many arguments to function ‘compAddTimeout’
star.c: In function ‘snowDisplayOptionChanged’:
star.c:656: error: incompatible type for argument 2 of ‘compAddTimeout’
star.c:656: error: too many arguments to function ‘compAddTimeout’
make: *** [build/star.lo] Error 1
compiling : star.c -> build/star.lostar.c: In function ‘updateSnowTextures’:
star.c:513: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
star.c:513: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
star.c:513: error: incompatible type for argument 3 of ‘compLogMessage’
star.c:517: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
star.c:517: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
star.c:517: error: incompatible type for argument 3 of ‘compLogMessage’
star.c: In function ‘snowInitScreen’:
star.c:589: error: incompatible type for argument 2 of ‘compAddTimeout’
star.c:589: error: too many arguments to function ‘compAddTimeout’
star.c: In function ‘snowDisplayOptionChanged’:
star.c:656: error: incompatible type for argument 2 of ‘compAddTimeout’
star.c:656: error: too many arguments to function ‘compAddTimeout’
make: *** [build/star.lo] Error 1
install   : /home/jason/.compiz/plugins/libtile.soinstall: cannot create regular file `/home/jason/.compiz/plugins/libtile.so': Permission denied
make: *** [install] Error 1
compiling : wallpaper.c -> build/wallpaper.lowallpaper.c: In function ‘initBackground’:
wallpaper.c:454: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
wallpaper.c:454: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
wallpaper.c:454: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/wallpaper.lo] Error 1
compiling : wallpaper.c -> build/wallpaper.lowallpaper.c: In function ‘initBackground’:
wallpaper.c:454: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
wallpaper.c:454: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
wallpaper.c:454: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/wallpaper.lo] Error 1

---

### Post by jskiddy19 on 2008-10-24
Here is the message I get for freewins, screensaver, photowheel, and wallpaper.

make install
compiling : wallpaper.c -> build/wallpaper.lowallpaper.c: In function ‘initBackground’:
wallpaper.c:454: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
wallpaper.c:454: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
wallpaper.c:454: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/wallpaper.lo] Error 1
jason@ubuntu:~/compiz/wallpaper$ cd ..

Any ideas?

---

### Post by Dalem50 on 2008-11-01
By the way, for the script, compiz-bcop for the "apt-get install" section needs to be replaced with compiz-fusion-bcop since compiz-bcop has been renamed. Just wanted to point it out :)

---

### Post by Dalem50 on 2008-11-01
Damis648,

You may want to change the script. In the installation part, please replace compiz-bcop to compiz-fusion-bcop since the package has been renamed.

-DaleM50

---

### Post by ruark1 on 2008-11-03
thanks dalem50 
that got everything working for me except the elements (fireflies, snow, leaves)
other than that it's great

---

### Post by soctu on 2008-11-17
> **soctu said:**
> Thanks for the link it worked (mostly) unfortunately Atlantis and the enviromentals do not work. Atlantis will not stay checked. I'm running Compiz 7.7:confused:

I fixed Atlantis! I first uninstalled the git compiz:

```
cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git
```

Then I downloaded the latest git compiz:

```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
```

Then I installed compiz git:

```
cd compiz-git
./compiz-git install
```

Now I had to chmod 777 the compiz-git directory to get this to run. If someone has a more secure alternative please let me know.

I got my info at: [http://www.mbastiaan.nl/compizgit.php](http://www.mbastiaan.nl/compizgit.php)
:guitar::popcorn::KS:KS:KS

---

### Post by jamefarm on 2008-11-19
I just wanted to reply to those that have had a problem with the atlatis (or other) plugins unchecking themselves.  I was able to fix it by downloading the compizplugins4.sh file, then changing compiz-bcop to compiz-fusion-bcop (as per previous replies)  then just running the script from a terminal.  Fixed the problem for me...Note however that not changing compiz-bcop to compiz-fusion-bcop resulted in errors for me.  I am running 8.10 if it's important.

---

### Post by Molochz on 2008-11-23
How do i run the script? Thanks in advance dude.

---

### Post by Fredizdman on 2008-12-02
Once you have downloaded the script, open it with whatever editor you like (vim,nano, etc....) and change "compiz-bcop" to "compiz-fusion-bcop" in the top line. Then just cd to whatever directory you downloaded it to and
```
sh ./compizplugins.sh
```

Good Luck!

---

### Post by 123456789mike on 2008-12-02
So download the script in the original, 1st, post?
Then change compiz-bcop to compiz-fusion-bcop.
Then what?                                
Oh and will this work for 8.10?
Thanks!

---

### Post by loomsen on 2008-12-02
> **Fredizdman said:**
> 
Good Luck!

:lolflag:

@ topic

Could anyone post a buildlog/list of plugins which are installed/the builddir after installation would even satisfy me.

I'd actually just want to know what **ls** shows after 
**sh ./compizplugins.sh** finished.

> Oh and will this work for 8.10?

I can't ensure this script will work, as I didn't try yet. However, if you do the following step by step it will work:
[Follow me, I'm a link](http://ubuntuforums.org/showpost.php?p=6295982&postcount=29)

---

### Post by 123456789mike on 2008-12-03
Thanks... haha I like your link's text. 
Thankfully I am not that braindead that I can't identify one ;)

Uhm, it turns out I am too braindead for your instructions...

Do you have a super, noob-friendly, tutorial?
Like.. maybe just:
1) copy/paste this code
2)now copy/paste
and so on ;)

Thank you!

---

### Post by loomsen on 2008-12-10
> **123456789mike said:**
> 
1) copy/paste this code



```

gksu synaptic

```

This is not for noobs.

---

### Post by Fredizdman on 2008-12-13
This script worked fine for me running Intrepid (8.10). I just changed that top line as mentioned earlier. Everything looks great.

---

### Post by draconastar on 2008-12-31
Hey guys, just a few questions, although I'm not sure anyone looks at this thread anymore.  

After using your script, and following all of the advice and modifications given in this thread, I'm still down to what I think are four plugins that aren't working correctly.  Elements, wallpaper, freewins and Photowheel.  I can't figure out why for the life of me, here's what Terminal spits at me after trying the script:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-dev is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
libglu1-mesa-dev is already the newest version.
libxss-dev is already the newest version.
git-core is already the newest version.
libcairo2 is already the newest version.
libcairo2-dev is already the newest version.
libcairomm-1.0-1 is already the newest version.
libcairo-perl is already the newest version.
libcairo-ruby1.8 is already the newest version.
libglitz1 is already the newest version.
libmono-cairo1.0-cil is already the newest version.
libmono-cairo2.0-cil is already the newest version.
libpixman-1-0 is already the newest version.
libpixman-1-dev is already the newest version.
libpixman-1-dev set to manually installed.
python-cairo is already the newest version.
The following NEW packages will be installed:
  compiz-fusion-bcop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8556B of archives.
After this operation, 119kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/universe compiz-fusion-bcop 0.6.0-1 [8556B]
Fetched 8556B in 11s (749B/s)       
Selecting previously deselected package compiz-fusion-bcop.
(Reading database ... 132835 files and directories currently installed.)
Unpacking compiz-fusion-bcop (from .../compiz-fusion-bcop_0.6.0-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-fusion-bcop_0.6.0-1_all.deb (--unpack):
 trying to overwrite `/usr/bin/bcop', which is also in package compiz-bcop
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-bcop_0.6.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
destination directory 'anaglyph' already exists.
destination directory 'atlantis2' already exists.
destination directory 'freewins' already exists.
destination directory 'photowheel' already exists.
destination directory 'screensaver' already exists.
destination directory 'snowglobe' already exists.
destination directory 'tile' already exists.
destination directory 'wallpaper' already exists.
install   : /home/daren/.compiz/plugins/libanaglyph.so
install   : /home/daren/.compiz/metadata/anaglyph.xml
install   : build/compiz-anaglyph.schema
install   : /home/daren/.compiz/plugins/libatlantis.so
install   : /home/daren/.compiz/metadata/atlantis.xml
install   : build/compiz-atlantis.schema
compiling : freewins.c -> build/freewins.lofreewins.c: In function ‘freewinsInitDisplay’:
freewins.c:337: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
freewins.c:337: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
freewins.c:337: error: incompatible type for argument 3 of ‘compLogMessage’
freewins.c:337: error: too few arguments to function ‘compLogMessage’
make: *** [build/freewins.lo] Error 1
compiling : freewins.c -> build/freewins.lofreewins.c: In function ‘freewinsInitDisplay’:
freewins.c:337: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
freewins.c:337: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
freewins.c:337: error: incompatible type for argument 3 of ‘compLogMessage’
freewins.c:337: error: too few arguments to function ‘compLogMessage’
make: *** [build/freewins.lo] Error 1
compiling : photo.c -> build/photo.lophoto.c: In function ‘photoTextureChange’:
photo.c:220: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
photo.c:220: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
photo.c:220: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/photo.lo] Error 1
compiling : photo.c -> build/photo.lophoto.c: In function ‘photoTextureChange’:
photo.c:220: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
photo.c:220: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
photo.c:220: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/photo.lo] Error 1
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)’
make: *** [build/screensaver.lo] Error 1
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)’
make: *** [build/screensaver.lo] Error 1
install   : /home/daren/.compiz/plugins/libsnowglobe.so
install   : /home/daren/.compiz/metadata/snowglobe.xml
install   : build/compiz-snowglobe.schema
install   : /home/daren/.compiz/plugins/libtile.so
install   : /home/daren/.compiz/metadata/tile.xml
install   : build/compiz-tile.schema
compiling : wallpaper.c -> build/wallpaper.lowallpaper.c: In function ‘initBackground’:
wallpaper.c:454: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
wallpaper.c:454: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
wallpaper.c:454: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/wallpaper.lo] Error 1
compiling : wallpaper.c -> build/wallpaper.lowallpaper.c: In function ‘initBackground’:
wallpaper.c:454: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
wallpaper.c:454: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
wallpaper.c:454: error: incompatible type for argument 3 of ‘compLogMessage’
make: *** [build/wallpaper.lo] Error 1
mkdir: cannot create directory `elements': File exists
--12:08:01--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `elements-most-recent.tar.gz.1'
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81,464 (80K) [application/x-gzip]

100%[====================================>] 81,464       142.80K/s             

12:08:05 (142.39 KB/s) - `elements-most-recent.tar.gz.1' saved [81464/81464]

compiling : elements.c -> build/elements.loelements.c: In function ‘elementMove’:
elements.c:266: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:266: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:266: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:266: error: too few arguments to function ‘compLogMessage’
elements.c: In function ‘updateElementTextures’:
elements.c:843: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:843: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:843: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:847: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:847: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:847: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:889: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:889: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:889: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:893: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:893: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:893: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:936: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:936: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:936: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:940: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:940: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:940: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:983: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:983: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:983: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:987: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:987: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:987: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:1030: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:1030: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:1030: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:1034: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:1034: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:1034: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c: In function ‘elementsInitScreen’:
elements.c:1114: error: incompatible type for argument 2 of ‘compAddTimeout’
elements.c:1114: error: too many arguments to function ‘compAddTimeout’
elements.c: In function ‘elementsDisplayOptionChanged’:
elements.c:1418: error: incompatible type for argument 2 of ‘compAddTimeout’
elements.c:1418: error: too many arguments to function ‘compAddTimeout’
make: *** [build/elements.lo] Error 1
compiling : elements.c -> build/elements.loelements.c: In function ‘elementMove’:
elements.c:266: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:266: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:266: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:266: error: too few arguments to function ‘compLogMessage’
elements.c: In function ‘updateElementTextures’:
elements.c:843: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:843: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:843: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:847: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:847: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:847: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:889: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:889: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:889: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:893: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:893: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:893: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:936: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:936: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:936: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:940: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:940: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:940: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:983: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:983: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:983: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:987: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:987: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:987: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:1030: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:1030: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:1030: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c:1034: warning: passing argument 1 of ‘compLogMessage’ from incompatible pointer type
elements.c:1034: warning: passing argument 2 of ‘compLogMessage’ makes pointer from integer without a cast
elements.c:1034: error: incompatible type for argument 3 of ‘compLogMessage’
elements.c: In function ‘elementsInitScreen’:
elements.c:1114: error: incompatible type for argument 2 of ‘compAddTimeout’
elements.c:1114: error: too many arguments to function ‘compAddTimeout’
elements.c: In function ‘elementsDisplayOptionChanged’:
elements.c:1418: error: incompatible type for argument 2 of ‘compAddTimeout’
elements.c:1418: error: too many arguments to function ‘compAddTimeout’
make: *** [build/elements.lo] Error 1
```

Sorry for the wall of text, but I don't know what to make of all of this.  Any help would be greatly appreciated!

---

### Post by draconastar on 2008-12-31
Ugh, in my attempts to remedy the situation myself, I have mucked this up pretty bad.  

I decided I was going to try and uninstall everything compiz related, so I went into Synaptic, searched "compiz" and removed everything with a green block by it.  When I reloaded, strangely, a lot of my options for key bindings in my Key Bindings menu were gone.  

Regardless, I reinstalled Compiz by downloading compizconfig-settings-manager, and not getting emerald since I hadn't gotten rid of it to begin with.  This worked, but I had almost no settings to choose from in the Advanced Desktop Settings, when I had installed the same way originally and had several.  Thinking it may have had to do with plugins, I followed the instructions given earlier in this thread to use compiz-git.  This process took a long time, and has left compiz crippled.  When I try to click on Advanced Desktop Settings, nothing happens.  When I try to click on the Fusion Icon, nothing happens.  When I try to load the icon through Terminal, it gave me a strange reason why it wouldn't work.  When I try to go through Appearance options and click "Extra", it tells me "Failed to execute child process "compiz" (No such file or directory)", when I had no idea the built in effects had anything to do with compiz.  Recently my key binding options came back, which is a plus, but I'm still confused about compiz.  Is there an easy way to revert to the way I started and get rid of all of the crap that's getting in the way?  I really hope someone reads this thread.  O_o

---

### Post by ellalan on 2008-12-31
Hi Draconastar 
Do not despair,go to synaptics and check ccsm,simple ccsm and fusion-icon for installation. You can leave the visual effects settings "normal" for the time being.
See what happens and if you want I can tell you how to install Compiz-git 0.7.9 version which is very easy to install and you do not need to uninstall your old version. Let me know if you are interested, It works well for me. Its your call.

---

### Post by J03y on 2008-12-31
Does these extra plugins work with Intrepid? Just thought of asking before downloading and installing the plugins... just in case :)

---

### Post by draconastar on 2008-12-31
Thank you Ellalan!  For some reason that seemed to work for me.  After getting the icon to work, I reloaded the Windows Manager, which made my effects start working again.  :D  

Now, the problem I run into is that I want some plugins, but the script did not work for me, nor did compiz-git last time I used that.  Is there another way to put the plugins installed?

---

### Post by pancham on 2009-01-01
I downloaded the file but how to install it....

---

### Post by ellalan on 2009-01-01
> **pancham said:**
> I downloaded the file but how to install it....
You have to edit the downloaded file by changing "compiz-bcop" to "compiz-fusion-bcop.
> cd Desktop
chmod +x compizplugins.sh
./compizplugins.sh
One line at a time in Terminal.HTH.

---

### Post by ellalan on 2009-01-01
Hi Draconastar
Could you tell me what graphics you have, what is your RAM because certain effects need good graphics to work. You have to tell what OS you are on as well, it is very useful if you provide all the information about your hardware when you look for answers. 
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)
[http://www.mbastiaan.nl/compizgit.php](http://www.mbastiaan.nl/compizgit.php)
have a look in these links and let me know if that helps, if not look at this link but I have to warn you that its in French but do not panic, if you are using Firefox, install an add on "Translator" and you can use that to translate the page. However you do not need to uninstall your current compiz at all. That script will uninstall the old one and install everything for you. But make sure you back up all important data from your computer.
[http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1)
If you are in any doubt,please ask for more information. HTH.

---

### Post by draconastar on 2009-01-01
GForce 7600 GTX with 512MB of memory, and I have 1GB of RAM in this computer.  Also, I'm running Ubuntu 8.04, kernel 2.6.24-22-generic.  

Thank you for all of your help.  :KS

---

### Post by ellalan on 2009-01-01
Your hardware seems fine, now go to the link I gave previously(French) and translate it and read, then you can download it following the instructions.
Once it stopped go to your Home folder you will see a file "cfinstall.sh", double click on that and click "Run-in-Terminal", it will uninstall the current version compiz and will install the new version, it will request you whether you want it to restart the computer(in French) click OK. 
HTH.
PS: When you get a list of options to install just tick only "compiz-git"

---

### Post by draconastar on 2009-01-01
After translating the french post and following the instructions given there, I am in worse shape than when I started.  The fusion-icon works, and is enabled on startup.  Also, all of the effects are available in the config menu.  

But none of them work. 

My windows are left without borders so I can't close them, none of the animations are working, several of my key bindings are missing, and the only thing I can do to make them manageable is to enable metacity as the window handler so that I can even do anything.

What's making it so that none of the effects that I can see are working?  They're clearly there, because I can see them in the config menu, but none of them work.  Help?

---

### Post by ellalan on 2009-01-01
Uncheck all effects and start enabling one by one and click the brush sign on the far right to set it to the default value, the window boarder problem I did what you are doing now(by switching to metacity from compiz) and I succeeded in getting rid of that after third install of this version of compiz. I am using the original nvidia driver provided by the system(version 169.12). I have attached some screen shots of some bindings for you to try.HTH.

---

### Post by fatpeoplefloat on 2009-01-01
I'm really sorry guys, I'm really new to the the whole linux/Ubuntu thing, how do i install these plug ins, they sound great and i think I've seen them on youtube, I'd love to have them but i don't know how!!

---

### Post by ellalan on 2009-01-01
> **fatpeoplefloat said:**
> I'm really sorry guys, I'm really new to the the whole linux/Ubuntu thing, how do i install these plug ins, they sound great and i think I've seen them on youtube, I'd love to have them but i don't know how!!
Welcome to the forum, you need to install compiz-config-settings-manager, Fusion-icon and simple-ccsm in synaptics.
System-> Administration-> synaptic package manager.
There are many posts in this forum, read as much as possible. This link is useful:[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by draconastar on 2009-01-01
Ellalan, going back through each setting and changing them to default did not help.  No effects are active, still.  The key bindings set up in the configuration window also don't work, as the effects don't work as well.  

Is there some core file that could be missing somewhere?  I'd run a compiz-check, but for some reason I can't access that site.

---

### Post by ellalan on 2009-01-01
Did you try this link, I just checked and its live.
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)
I do not know of any core files and I am running out of ideas but be patient someone will come up with a solution and I'll do some searching as well.

EDIT: what visual effect you have now?(under system->Appearance)

---

### Post by draconastar on 2009-01-01
Ah, yeah, that link is one of many I've tried.  In another thread, Forlong is actually trying to help me as well.  When I click on that link, I get "Status: 500 Internal Server Error Content-Type: text/html", when I don't know what that means.

Currently, I have "none" checked in appearances, because it's the only way that I can get my window borders to work.  

I really appreciate your help, I'll try to remain patient and be as helpful as I can.  :D

---

### Post by ellalan on 2009-01-02
Could you change the visual effects to "normal" and try, you won't get compiz working with "none" marked in visual effects.

---

### Post by fatpeoplefloat on 2009-01-02
> **ellalan said:**
> Welcome to the forum, you need to install compiz-config-settings-manager, Fusion-icon and simple-ccsm in synaptics.
System-> Administration-> synaptic package manager.
There are many posts in this forum, read as much as possible. This link is useful:[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

i have done this, as i saw this on the internet this was my fisrt port of call on ubuntu, but how do actually add these plugins to the compiz fusion I already own?:(

---

### Post by ellalan on 2009-01-02
> **fatpeoplefloat said:**
> i have done this, as i saw this on the internet this was my fisrt port of call on ubuntu, but how do actually add these plugins to the compiz fusion I already own?:(
See this link whether it helps you:
[http://forum.compiz-fusion.org/showthread.php?p=68054](http://forum.compiz-fusion.org/showthread.php?p=68054)

---

### Post by draconastar on 2009-01-02
Having either normal or extra checked makes my borders go away, which is why I'm not using it at the moment.

---

### Post by ellalan on 2009-01-02
> **draconastar said:**
> Having either normal or extra checked makes my borders go away, which is why I'm not using it at the moment.
When your window borders miss, right click the fusion icon and change window manager to metacity and you'll get the window borders, now switch back to compiz window manager.

---

### Post by fatpeoplefloat on 2009-01-02
i've done all of this and a fraction of it seems to have worked, i jave the "atlantis" plugin within the advance effects area, but none of the others seem to have worked, its really getting me annoyed, but considering i fairly new to ubuntu, i dont want to make anything go wrong.

---

### Post by ellalan on 2009-01-02
> **fatpeoplefloat said:**
> i've done all of this and a fraction of it seems to have worked, i jave the "atlantis" plugin within the advance effects area, but none of the others seem to have worked, its really getting me annoyed, but considering i fairly new to ubuntu, i dont want to make anything go wrong.
What effects are not working for you? Certain effects need more resources(graphics),do you have dedicated graphics?
Read other posts and find out more about compiz and related problems others are encountering.

---

### Post by draconastar on 2009-01-02
Switching back over to Compiz as the window manager makes my borders disappear again, and when I go into my Appearance preferences it turns out that it has Extra checked, which I guess means that they are linked.

---

### Post by ellalan on 2009-01-02
> **draconastar said:**
> Switching back over to Compiz as the window manager makes my borders disappear again, and when I go into my Appearance preferences it turns out that it has Extra checked, which I guess means that they are linked.
Try this
Right click compiz-fusion icon under Select Window manager select Compiz,under select window decorator select GTK.
Press Alt+F2, enter the following
> compiz --replace

---

### Post by draconastar on 2009-01-04
compiz --replace didn't work for me the last time I tried it, I can't remember why right now, but I'm not currently on my Ubuntu machine.  I'll be back with it later tonight, and will post again as to the results.  Thanks.  :D

---

### Post by draconastar on 2009-01-04
compiz --replace completes, but makes my window borders go away.  It's basically the same thing has going in and checking Extra, or clicking on the fusion icon and choosing compiz as the window manager.

---

### Post by prshah on 2009-01-05
> **draconastar said:**
> compiz --replace completes, but makes my window borders go away.  It's basically the same thing has going in and checking Extra, or clicking on the fusion icon and choosing compiz as the window manager.

Make sure both window decorators are running: compiz-decorater and gtk-window-decorator ```
ps -e| grep -i deco
12216 ?        00:00:00 compiz-decorato
12218 ?        00:00:02 gtk-window-deco

``` If any are not running, try executing it manually; eg, Press Alt+F2 then give the command```
compiz-decorator
```

If you try running these from a terminal, you should be aware that they will be terminated when you close the terminal.

---

### Post by draconastar on 2009-01-05
The first command you gave me returns with nothing:

```
daren@daren-desktop:~$ ps -e| grep -i deco
daren@daren-desktop:~$ 

```

The second command informs me that I don't have compiz-core installed, which is strange:

```
daren@daren-desktop:~$ compiz-decorator
The program 'compiz-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz-decorator: command not found

```

According to Synaptic, I don't have *anything* compiz related installed after using the script.

---

### Post by prshah on 2009-01-05
> **draconastar said:**
> 
```
daren@daren-desktop:~$ ps -e| grep -i deco
daren@daren-desktop:~$ 

```
According to Synaptic, I don't have *anything* compiz related installed after using the script.

If you have compiled compiz from the source code this is understandable, but not otherwise. Why not just try to install the compiz-decorator as guided and then see what happens? Or just running gtk-window-decorator?

---

### Post by draconastar on 2009-01-05
It was "installed" using a script provided earlier in this thread, page 17 if I'm not mistaken.  It never went through the package manager to install the components, which is why, I suppose, it doesn't see it.  

I'm currently using whatever the default, not flashy window decorator is for Ubuntu, because that's the only thing that's working for me right now.  Any other options checked, and my window borders disappear.

---

### Post by MaindotC on 2009-01-06
I've read the posts of draconstar and I'd like to ask help as well.  I'm getting the error:
```

compiling : snow.c -> build/snow.losnow.c: In function &#8216;updateSnowTextures&#8217;:
snow.c:459: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
snow.c:459: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
snow.c:459: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
snow.c:463: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
snow.c:463: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
snow.c:463: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
snow.c: In function &#8216;snowInitScreen&#8217;:
snow.c:545: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
snow.c:545: error: too many arguments to function &#8216;compAddTimeout&#8217;
snow.c: In function &#8216;snowDisplayOptionChanged&#8217;:
snow.c:613: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
snow.c:613: error: too many arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/snow.lo] Error 1

```
which is similar to draconastar's.

---

### Post by setsuna on 2009-01-20
> **brsmits said:**
> Strange, when I

./compizplugins.sh

it Gets the files fine, seems to unpack them with no problem, but then it begins doing:


Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Initialized empty Git repository in /home/smitz/compiz/anaglyph/.git/
anongit.compiz-fusion.org[0: 195.114.19.35]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)
fetch-pack from 'git://anongit.compiz-fusion.org/users/wodor/anaglyph' failed.
Initialized empty Git repository in /home/smitz/compiz/atlantis2/.git/
.
.
.


with all the packages.  Any ideas?  I recently installed Hardy, is there a quick fix to this?

Ideas?

yaa, i've same problem too,
but yesterday, when i'm googling, it's said about proxy issue when use git,

somebody help me .. 
sorry for my poor english
~thx~

---

### Post by Stinja on 2009-03-23
thank you so much, this worked really well. i couldnt get these plugins and was distraught about it. but this worked :D :KS

---

### Post by MaindotC on 2009-03-23
Still not working for me. I wish someone would please help me.

---

### Post by Joshua Wells on 2009-04-07
> **Kaneda187 said:**
> can anyone help? its something about permission denied ...? Y'all know better than me! please guys help!!

i did the same thing, you need to run it as root. 
cd Desktop
sh [name].sh
enter

---

### Post by MaindotC on 2009-04-08
Yeah, doesn't work.  I really wish one of you developers would be kind enough to help out those of us that are having build/snow.lo errors.  Does no one else watch this thread?

---

### Post by Saints9 on 2009-04-08
Hey im new here and im new at ubuntu, first i got a error message that i didnt have compiz installed so i installed compiz-dev and then i got something about bcop so i installed fusion-bcop and now i get some Error package 

senshow@ubuntu:~/Desktop$ sh compizplugins4.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate
Initialized empty Git repository in /home/senshow/compiz/anaglyph/.git/
remote: Counting objects: 121, done.
remote: Compressing objects: 100% (117/117), done.
remote: Total 121 (delta 60), reused 0 (delta 0)
Receiving objects: 100% (121/121), 25.88 KiB, done.
Resolving deltas: 100% (60/60), done.
Initialized empty Git repository in /home/senshow/compiz/atlantis2/.git/
remote: Counting objects: 869, done.
remote: Compressing objects: 100% (865/865), done.
remote: Total 869 (delta 596), reused 0 (delta 0)
Receiving objects: 100% (869/869), 2.92 MiB | 1315 KiB/s, done.
Resolving deltas: 100% (596/596), done.
Initialized empty Git repository in /home/senshow/compiz/freewins/.git/
remote: Counting objects: 1190, done.
remote: Compressing objects: 100% (1186/1186), done.
remote: Total 1190 (delta 826), reused 0 (delta 0)
Receiving objects: 100% (1190/1190), 274.40 KiB, done.
Resolving deltas: 100% (826/826), done.
Initialized empty Git repository in /home/senshow/compiz/photowheel/.git/
remote: Counting objects: 44, done.
remote: Compressing objects: 100% (41/41), done.
Receiving objects: 100% (44/44), 13.36 KiB, done.
remote: Total 44 (delta 22), reused 0 (delta 0)
Resolving deltas: 100% (22/22), done.
Initialized empty Git repository in /home/senshow/compiz/screensaver/.git/
remote: Counting objects: 176, done.
remote: Compressing objects: 100% (172/172), done.
remote: Total 176 (delta 102), reused 0 (delta 0)
Receiving objects: 100% (176/176), 44.75 KiB, done.
Resolving deltas: 100% (102/102), done.
Initialized empty Git repository in /home/senshow/compiz/snowglobe/.git/
remote: Counting objects: 99, done.
remote: Compressing objects: 100% (96/96), done.
remote: Total 99 (delta 58), reused 0 (delta 0)
Receiving objects: 100% (99/99), 154.58 KiB, done.
Resolving deltas: 100% (58/58), done.
Initialized empty Git repository in /home/senshow/compiz/tile/.git/
fatal: The remote end hung up unexpectedly
Initialized empty Git repository in /home/senshow/compiz/wallpaper/.git/
remote: Counting objects: 252, done.
remote: Compressing objects: 100% (248/248), done.
remote: Total 252 (delta 126), reused 0 (delta 0)
Receiving objects: 100% (252/252), 48.41 KiB, done.
Resolving deltas: 100% (126/126), done.
convert   : anaglyph.xml.in -> build/anaglyph.xml
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.h
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.c
schema    : build/anaglyph.xml -> build/compiz-anaglyph.schema
compiling : anaglyph.c -> build/anaglyph.lo/bin/sh: libtool: not found
make: *** [build/anaglyph.lo] Error 127
compiling : anaglyph.c -> build/anaglyph.lo/bin/sh: libtool: not found
make: *** [build/anaglyph.lo] Error 127
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : fish2.c -> build/fish2.lo/bin/sh: libtool: not found
make: *** [build/fish2.lo] Error 127
compiling : fish2.c -> build/fish2.lo/bin/sh: libtool: not found
make: *** [build/fish2.lo] Error 127
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.
convert   : photo.xml.in -> build/photo.xml
bcop'ing  : build/photo.xml -> build/photo_options.h
bcop'ing  : build/photo.xml -> build/photo_options.c
schema    : build/photo.xml -> build/compiz-photo.schema
compiling : photo.c -> build/photo.lo/bin/sh: libtool: not found
make: *** [build/photo.lo] Error 127
compiling : photo.c -> build/photo.lo/bin/sh: libtool: not found
make: *** [build/photo.lo] Error 127
Makefile:58: *** [ERROR] No package 'xscrnsaver' found.  Stop.
Makefile:58: *** [ERROR] No package 'xscrnsaver' found.  Stop.
convert   : snowglobe.xml.in -> build/snowglobe.xml
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.h
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.c
schema    : build/snowglobe.xml -> build/compiz-snowglobe.schema
compiling : snowglobe.c -> build/snowglobe.lo/bin/sh: libtool: not found
make: *** [build/snowglobe.lo] Error 127
compiling : snowglobe.c -> build/snowglobe.lo/bin/sh: libtool: not found
make: *** [build/snowglobe.lo] Error 127
cd: 40: can't cd to tile
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
cd: 44: can't cd to wallpaper
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `elements': Permission denied
cd: 49: can't cd to elements
--2009-04-08 21:42:19--  [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)
Resolving [www.elementsplugin.com](www.elementsplugin.com)... 69.89.31.238
Connecting to [www.elementsplugin.com|69.89.31.238|:80](www.elementsplugin.com|69.89.31.238|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

Some help would be appreciated, however i have one more question... How do I use these plugins after I've installed them :S I've looked around in CCSM but i cant find them anywhere :S.

---

### Post by Psychopump on 2009-04-08
I am having some issues too:  

```
loki@loki-laptop:~/downloads$ chmod +x compizplugins3.sh
loki@loki-laptop:~/downloads$ ./compizplugins3.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate
./compizplugins3.sh: line 5: git: command not found
./compizplugins3.sh: line 6: git: command not found
./compizplugins3.sh: line 7: git: command not found
./compizplugins3.sh: line 8: git: command not found
./compizplugins3.sh: line 9: git: command not found
./compizplugins3.sh: line 10: git: command not found
./compizplugins3.sh: line 11: git: command not found
./compizplugins3.sh: line 12: git: command not found
./compizplugins3.sh: line 16: cd: anaglyph: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 20: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 24: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 28: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 32: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 36: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 40: cd: tile: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins3.sh: line 44: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `elements': Permission denied
./compizplugins3.sh: line 49: cd: elements: No such file or directory
--2009-04-08 21:57:47--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
loki@loki-laptop:~/downloads$ 
loki@loki-laptop:~/downloads$
```

---

### Post by Psychopump on 2009-04-21
*bump*

Any help, please?

---

### Post by tjwoosta on 2009-04-23
do you guys have build-essential installed?

---

### Post by caligula2 on 2009-04-29
try opening compizplugins.sh in text editor and in the first line that says "sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core" change "compiz-bcop" to "compiz-fusion-bcop." so the first line should look like:

sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core

---

### Post by alejobar on 2009-04-29
I tried to install this in Intrepid and everything went ok just change the install script like everybody else said. But now I tried to installed in hardy with all the updates, and I got an error at the end, so how can I remove the incomplete installation?

---

### Post by borramakot on 2009-04-29
Works good, very useful. However, I had to remove the compiz-bcop from the first line, because it appears to have been replaced. Thanks!

---

### Post by ShiroKitsune on 2009-05-01
Hi ummm Im still new to Ubuntu and Compiz, but its alot better then windows CubeDesktop. Okay friends, I was wondering how do i get the atlantis plugin for cube gears, i saw it on YouTube, and now i want it so bad :|. Can anyone tell me witch plugin pack has it?:?

;) If ya tell me i'll be your best friend:lolflag:

---

### Post by hockman5 on 2009-05-06
Anyone have a different script that will work with Jaunty???
I mainly want the fireflies plugin....

---

### Post by MaindotC on 2009-05-08
I PM'd the OP and he said he doesn't watch the thread anymore and he is working on other projects so I doubt we'll get any help w/ this.  Especially since it has three-pages of posts, other users won't visit this thread b/c they'll figure there are already tons of people in the thread helping us out.

---

### Post by tjwoosta on 2009-05-08
i found a .deb for i386 on this page although i dont use ubuntu anymore so i cant test it myself

[https://launchpad.net/ubuntu/jaunty/i386/compiz-fusion-plugins-unsupported/0.8.2-1ubuntu1]("https://launchpad.net/ubuntu/jaunty/i386/compiz-fusion-plugins-unsupported/0.8.2-1ubuntu1")

and here is the direct link to the .deb

[http://launchpadlibrarian.net/26378496/compiz-fusion-plugins-unsupported_0.8.2-1ubuntu1_i386.deb]("http://launchpadlibrarian.net/26378496/compiz-fusion-plugins-unsupported_0.8.2-1ubuntu1_i386.deb")

---

### Post by bandgeek on 2009-05-09
Hopefully this will solve some problems. Made some changes to the script and worked like a charm on Jaunty Jackalope.

Turns out I had the plugins installed from synaptic. I suggest that you use compiz-fusion-plugins-unsupported.

However you can still try the script.

---

### Post by tatw on 2009-05-12
> **NDenney said:**
> Hopefully this will solve some problems. Made some changes to the script and worked like a charm on Jaunty Jackalope.
Only Anaglyph installed :confused:

---

### Post by bandgeek on 2009-05-12
Well actually not that many changes just changed the downloaded packages. Sorry don't have that much experience yet. One question. Are you using proprietary video drivers? If yes try uninstalling those then reinstalling the plugins. Also in Synaptic there is a package called compiz-fusion-plugins-unsupported.

Turns out I had this installed and ran the script. So try Synaptic and see if that does it.

---

### Post by tjwoosta on 2009-05-12
Last time I checked the unsupported package thats in synaptic was for version 7.8 not 8.2, unless they finally updated it.

---

### Post by bandgeek on 2009-05-13
In the repositories it is 8.2.

---

### Post by moore.bryan on 2009-05-30
maybe you guys can help me; unfortunately, the compiz forums have been of no help. i've installed the extras, including screensaver, but that's the only one i really want and that's the only one which doesn't show-up in my compiz settings. any ideas?

---

### Post by moore.bryan on 2009-06-02
can anyone help me with this screensaver plugin?

nevermind... i git'd it and make installed; let's see if it works!

---

### Post by auto123 on 2009-07-29
hi,

I've been trying to get atlantis running for the last 3 hours and even with your sweet scripting I still get this error :(

```

tyler@tyler-laptop:~$ cd /home/tyler/atlantis
tyler@tyler-laptop:~/atlantis$ make
compiling : dolphin.c -> build/dolphin.lo/bin/sh: libtool: not found
make: *** [build/dolphin.lo] Error 127
tyler@tyler-laptop:~/atlantis$ make install
compiling : dolphin.c -> build/dolphin.lo/bin/sh: libtool: not found
make: *** [build/dolphin.lo] Error 127
tyler@tyler-laptop:~/atlantis$ 

```

any help would be aprreciated, I've tried and tried again and redownloaded a heck of a lot too, and still I can't get it to work :(

thanks,
-Tyler

---

### Post by MaindotC on 2009-07-30
Well, if libtool isn't found, then install it.  Duh!

I'm still getting the same problem:
```

compiling : snow.c -> build/snow.losnow.c: In function &#8216;updateSnowTextures&#8217;:
snow.c:459: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
snow.c:459: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
snow.c:459: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
snow.c:463: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
snow.c:463: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
snow.c:463: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
snow.c: In function &#8216;snowInitScreen&#8217;:
snow.c:545: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
snow.c:545: error: too many arguments to function &#8216;compAddTimeout&#8217;
snow.c: In function &#8216;snowDisplayOptionChanged&#8217;:
snow.c:613: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
snow.c:613: error: too many arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/snow.lo] Error 1

```

---

### Post by Slasher The Great! on 2009-08-06
hi,
my name is slasher and im 10 years old.
I'm having some trouble installing you script, i keep getting errors.
unfortunatly I do not know how to print screen yet to show you the errors ](*,)

---

### Post by bandgeek on 2009-08-07
Instead of using the script open synaptic and install compiz-fusion-plugins-unsupported. I installs all of the same things without any errors.

---

### Post by WeAreTheSiNs on 2010-01-09
> **damis648 said:**
> The
compiz --replace &
causes a temporary bug in compiz which causes two instances of compiz to run at the same time. Do you think
```
killall compiz
killall compiz.real
compiz --replace &
```
would fix that without a reboot?

Yes it does fix it without a reboot :)

---

### Post by pigeondetective on 2010-03-07
```
 adam@adam-laptop:~/Desktop$ sh compizplugins4.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate
Initialized empty Git repository in /home/adam/compiz/anaglyph/.git/
remote: Counting objects: 121, done.
remote: Compressing objects: 100% (117/117), done.
remote: Total 121 (delta 60), reused 0 (delta 0)
Receiving objects: 100% (121/121), 25.88 KiB, done.
Resolving deltas: 100% (60/60), done.
Initialized empty Git repository in /home/adam/compiz/atlantis2/.git/
remote: Counting objects: 875, done.
remote: Compressing objects: 100% (871/871), done.
remote: Total 875 (delta 600), reused 0 (delta 0)
Receiving objects: 100% (875/875), 2.92 MiB | 1885 KiB/s, done.
Resolving deltas: 100% (600/600), done.
Initialized empty Git repository in /home/adam/compiz/freewins/.git/
remote: Counting objects: 1190, done.
remote: Compressing objects: 100% (1186/1186), done.
remote: Total 1190 (delta 826), reused 0 (delta 0)
Receiving objects: 100% (1190/1190), 274.40 KiB, done.
Resolving deltas: 100% (826/826), done.
Initialized empty Git repository in /home/adam/compiz/photowheel/.git/
remote: Counting objects: 44, done.
remote: Compressing objects: 100% (41/41), done.
remote: Total 44 (delta 22), reused 0 (delta 0)
Receiving objects: 100% (44/44), 13.37 KiB, done.
Resolving deltas: 100% (22/22), done.
Initialized empty Git repository in /home/adam/compiz/screensaver/.git/
remote: Counting objects: 176, done.
remote: Compressing objects: 100% (172/172), done.
remote: Total 176 (delta 102), reused 0 (delta 0)
Receiving objects: 100% (176/176), 44.75 KiB, done.
Resolving deltas: 100% (102/102), done.
Initialized empty Git repository in /home/adam/compiz/snowglobe/.git/
remote: Counting objects: 99, done.
remote: Compressing objects: 100% (96/96), done.
remote: Total 99 (delta 58), reused 0 (delta 0)
Receiving objects: 100% (99/99), 154.58 KiB, done.
Resolving deltas: 100% (58/58), done.
Initialized empty Git repository in /home/adam/compiz/tile/.git/
fatal: The remote end hung up unexpectedly
Initialized empty Git repository in /home/adam/compiz/wallpaper/.git/
fatal: The remote end hung up unexpectedly
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
convert   : photo.xml.in -> build/photo.xml
bcop'ing  : build/photo.xml -> build/photo_options.h
bcop'ing  : build/photo.xml -> build/photo_options.c
make: *** No rule to make target `build/photo.lo', needed by `c-build-objs'. Stop.
make: *** No rule to make target `build/photo.lo', needed by `c-build-objs'. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Makefile:48: *** [ERROR] Compiz not installed. Stop.
cd: 40: can't cd to tile
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
cd: 44: can't cd to wallpaper
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
mkdir: cannot create directory `elements': Permission denied
cd: 49: can't cd to elements
--2010-03-07 19:18:22--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
Resolving www.elementsplugin.com... 74.220.219.113
Connecting to www.elementsplugin.com|74.220.219.113|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.

```I get this error. Why does it say i havent got compiz installed? Have i missed something. ubuntu 9.04 and it definately is installed.

---

### Post by cocopuffz on 2010-04-14
I just tried the script and got the same error... I'm going to try that compiz-fusion-plugins-unsupported in synaptic and see if that works instead. Did you ever get your problem resolved?

---

### Post by LatinHacker on 2010-06-22
> **damis648 said:**
> I got bored and fed up while installing compiz plugins so i wrote this script to automatically install 12 of them: Anaglyph, Atlantis, Atlantis2, Fireflies, Freewins, Photowheel, Screensaver, Snow, Snowglobe, Stars, Tile, and Wallpaper.
Download the script below.

IMPORTANT NOTES!: DO [COLOR=Red]NOT[/COLOR] RUN THE SCRIPT AS ROOT AND YOU [COLOR=Red]MUST[/COLOR] REBOOT AFTER RUNNING THE SCRIPT OR THE PLUGINS WILL NOT FUNCTION PROPERLY.

Tested on Hardy with Compiz 0.7.4.

EDIT: Wow I cannot believe I forgot to upload the script... :popcorn:

**UPDATE: I realized it would do good to update this first post for new versions of the script. The newest version is version 4 on the 4th page.**

I feel like a dumb****, but how do *.sh script run?

---

### Post by MaindotC on 2010-06-22
You execute the script by typing:
```

./script.sh

```

---

### Post by Goldfire123 on 2010-09-12
Can Someone help me install the plugins?
I'm running on ubuntu 10.04:

steven@ubuntu:~$ sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core libcairo2 libcairo2-dev libcairomm-1.0-1 libcairo-perl libcairo-ruby1.8 libglitz1 libmono-cairo1.0-cil libmono-cairo2.0-cil libpixman-1-0 libpixman-1-dev python-cairo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate
steven@ubuntu:~$ cd
steven@ubuntu:~$ mkdir -p compiz
steven@ubuntu:~$ cd compiz
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
fatal: destination path 'anaglyph' already exists and is not an empty directory.
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
Initialized empty Git repository in /home/steven/compiz/atlantis2/.git/
fatal: The remote end hung up unexpectedly
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/warlock/freewins
Initialized empty Git repository in /home/steven/compiz/freewins/.git/
remote: Counting objects: 1202, done.
remote: Compressing objects: 100% (1198/1198), done.
remote: Total 1202 (delta 827), reused 0 (delta 0)
Receiving objects: 100% (1202/1202), 304.56 KiB | 17 KiB/s, done.
Resolving deltas: 100% (827/827), done.
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/b0le/photowheel
Initialized empty Git repository in /home/steven/compiz/photowheel/.git/
remote: Counting objects: 62, done.
remote: Compressing objects: 100% (59/59), done.
remote: Total 62 (delta 28), reused 0 (delta 0)
Receiving objects: 100% (62/62), 19.32 KiB | 16 KiB/s, done.
Resolving deltas: 100% (28/28), done.
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
Initialized empty Git repository in /home/steven/compiz/screensaver/.git/
remote: Counting objects: 197, done.
remote: Compressing objects:  68% (131/19Receiving objects:  28% (56/197), 20.00remote: Compressing objeReceiving objects:  42% (83/197), 36.00 KiB | 13 KiB/s  remote: Compressing objects:  78% (Receiving objects:  80% (158/197), 44.00 KiB remote: Compressing objects: 100% Receiving objects:  84% (166/197), 44.00 KiB |(192/192), done.
remote: Total 197 (delta 111), reused 0 (delta 0)
Receiving objects: 100% (197/197), 54.02 KiB | 11 KiB/s, done.
Resolving deltas: 100% (111/111), done.
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
Initialized empty Git repository in /home/steven/compiz/snowglobe/.git/
remote: Counting objects: 110, done.
remote: Compressing objects: 100% (107/107), done.
remote: Total 110 (delta 59), reused 0 (delta 0)
Receiving objects: 100% (110/110), 204.38 KiB | 17 KiB/s, done.
Resolving deltas: 100% (59/59), done.
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
Initialized empty Git repository in /home/steven/compiz/tile/.git/
fatal: The remote end hung up unexpectedly
steven@ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper
Initialized empty Git repository in /home/steven/compiz/wallpaper/.git/
fatal: The remote end hung up unexpectedly
steven@ubuntu:~/compiz$ cd ..
steven@ubuntu:~$ chmod 777 compiz
steven@ubuntu:~$ cd compiz
steven@ubuntu:~/compiz$ cd anaglyph
steven@ubuntu:~/compiz/anaglyph$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:~/compiz/anaglyph$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:~/compiz/anaglyph$ cd ..
steven@ubuntu:~/compiz$ cd atlantis2
bash: cd: atlantis2: No such file or directory
steven@ubuntu:~/compiz$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:~/compiz$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:~/compiz$ cd ..
steven@ubuntu:~$ cd freewins
bash: cd: freewins: No such file or directory
steven@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:~$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:~$ cd ..
steven@ubuntu:/home$ cd photowheel
bash: cd: photowheel: No such file or directory
steven@ubuntu:/home$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/home$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:/home$ cd ..
steven@ubuntu:/$ cd screensaver
bash: cd: screensaver: No such file or directory
steven@ubuntu:/$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:/$ cd ..
steven@ubuntu:/$ cd snowglobe
bash: cd: snowglobe: No such file or directory
steven@ubuntu:/$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:/$ cd ..
steven@ubuntu:/$ cd tile
bash: cd: tile: No such file or directory
steven@ubuntu:/$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:/$ cd ..
steven@ubuntu:/$ cd wallpaper
bash: cd: wallpaper: No such file or directory
steven@ubuntu:/$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/$ make install
make: *** No rule to make target `install'.  Stop.
steven@ubuntu:/$ cd ..
steven@ubuntu:/$ mkdir elements
mkdir: cannot create directory `elements': Permission denied
steven@ubuntu:/$ cd elements
bash: cd: elements: No such file or directory
steven@ubuntu:/$ wget [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)
--2010-09-12 09:45:26--  [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)
Resolving [www.elementsplugin.com](www.elementsplugin.com)... 74.220.219.113
Connecting to [www.elementsplugin.com|74.220.219.113|:80](www.elementsplugin.com|74.220.219.113|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
steven@ubuntu:/$ tar -xf elements-most-recent.tar.gz
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
steven@ubuntu:/$ make
make: *** No targets specified and no makefile found.  Stop.
steven@ubuntu:/$ make install
make: *** No rule to make target `install'.  Stop.
Any help would be appreciated:p

---

### Post by imginy on 2010-10-28
> **damis648 said:**
> I am posting version 4 of the script that should fix any issues about errors regarding cairo-xlib errors.
Hi there I am trying to download this script but it says to me unable to save this file please contact admin or try again later what do I do?

---

### Post by soad6 on 2010-11-28
Getting this issue trying to run the script on Linux ubuntu 10.10. it seems libglitz is missing or cant be located as well as compiz-bcop. Even though I have compiz-bcop installed and libglitz1 has been removed from the repos since ubuntu 10.04 LTS. Not sure what to do. I have the .deb package installed for snow and elements and a few others I just want the screensaver plugin. Thanks if you can help.

~/Downloads$ ./compizplugins4.sh
[sudo] password for needlez: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package compiz-bcop
E: Unable to locate package libglitz1
Initialized empty Git repository in /home/needlez/compiz/anaglyph/.git/
remote: Counting objects: 131, done.
remote: Compressing objects: 100% (127/127), done.
remote: Total 131 (delta 62), reused 0 (delta 0)
Receiving objects: 100% (131/131), 30.02 KiB, done.
Resolving deltas: 100% (62/62), done.
Initialized empty Git repository in /home/needlez/compiz/atlantis2/.git/
fatal: The remote end hung up unexpectedly
Initialized empty Git repository in /home/needlez/compiz/freewins/.git/
remote: Counting objects: 1208, done.
remote: Compressing objects: 100% (1204/1204), done.
remote: Total 1208 (delta 831), reused 0 (delta 0)
Receiving objects: 100% ( 1208/1208 ), 305.04 KiB | 227 KiB/s, done.
Resolving deltas: 100% (831/831), done.
Initialized empty Git repository in /home/needlez/compiz/photowheel/.git/
remote: Counting objects: 70, done.
remote: Compressing objects: 100% (67/67), done.
remote: Total 70 (delta 32), reused 0 (delta 0)
Receiving objects: 100% (70/70), 20.32 KiB, done.
Resolving deltas: 100% (32/32), done.
Initialized empty Git repository in /home/needlez/compiz/screensaver/.git/
remote: Counting objects: 209, done.
remote: Compressing objects: 100% (204/204), done.
remote: Total 209 (delta 119), reused 0 (delta 0)
Receiving objects: 100% (209/209), 54.97 KiB, done.
Resolving deltas: 100% (119/119), done.
Initialized empty Git repository in /home/needlez/compiz/snowglobe/.git/
remote: Counting objects: 113, done.
remote: Compressing objects: 100% (110/110), done.
remote: Total 113 (delta 60), reused 0 (delta 0)
Receiving objects: 100% (113/113), 204.71 KiB | 279 KiB/s, done.
Resolving deltas: 100% (60/60), done.
Initialized empty Git repository in /home/needlez/compiz/tile/.git/
fatal: The remote end hung up unexpectedly
Initialized empty Git repository in /home/needlez/compiz/wallpaper/.git/
fatal: The remote end hung up unexpectedly
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 20: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 24: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 28: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 32: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 36: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 40: cd: tile: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compizplugins4.sh: line 44: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `elements': Permission denied
./compizplugins4.sh: line 49: cd: elements: No such file or directory
--2010-11-28 18:33:31--  [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)
Resolving [www.elementsplugin.com](www.elementsplugin.com)... 74.220.219.113
Connecting to [www.elementsplugin.com|74.220.219.113|:80](www.elementsplugin.com|74.220.219.113|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
elements-most-recent.tar.gz: Permission denied

Cannot write to `elements-most-recent.tar.gz' (Permission denied).
tar: elements-most-recent.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

---

### Post by soad6 on 2010-11-28
[COLOR="Red"]THESE FILES ARE INCORRECT SORRY DOWNLOAD SCRIPT FROM JOHNNYG713 AND FOLLOW MY INSTRUCTIONS PAGE 24 INSTRUCTIONS TITLE COLOR BLUE[/COLOR]

Ok so I changed somethings in the script like instead of compiz-bcop it should be compiz-fusion-bcop
and removed libglitz1 so it could run and had to run as sudo to let it compile all the way the only issue now is that even after that i still dont see the plugins so does anyone have any info on how to get the screensaver plugin for compiz on ubuntu 10.10?? Thanks for the help.

Also attached my modified version of the script not sure what to do to fix the fact that libglitz1 has been removed from repos totally so not sure what to replace it with. Thanks again for any help.

---

### Post by soad6 on 2010-11-28
**[COLOR="Red"]DISREGARD POST LOOK FOR POST #236 THAT POST FIXES ALL ISSUES WITH EXTRA ADDONS[/COLOR]**
Ok nvm it does add the extras element plugin... but not sure if screensaver plugin is installed. MUST RUN SCRIPT AS SUDO. then must run 
killall compiz
compiz --replace &
after this you should see an elements box in the extras area this works.
Also dont try to install the .deb or synaptic version of these plugins as those are broken and dont work.

---

### Post by JOHNNYG713 on 2010-11-28
Try this ! Thanks to Scott Moreau ! make it executable.:p Installs all dependacies and compiz plugins ! Even Wizard !:p

---

### Post by soad6 on 2010-11-28
[COLOR="Red"]DISREGARD THIS POST!! FIXED!![/COLOR]

Getting this error when running. Made sure I had all dependencies and still getting this error. How can I fix this and thank you very much.

 ./compiz-addons.sh
i = Install s = Skip u = Uninstall a = Install all remaining without prompting q = Quit
What would you like to do for anaglyph? i/s/u/a/q: i
Existing source for anaglyph detected.
Already up-to-date.
Building anaglyph..
removing  : ./build
convert   : anaglyph.xml.in -> build/anaglyph.xml
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.h
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.c
schema    : build/anaglyph.xml -> build/compiz-anaglyph.schema
compiling : anaglyph.c -> build/anaglyph.lo
compiling : build/anaglyph_options.c -> build/anaglyph_options.lo
linking   : build/libanaglyph.la
Installing..
install   : /home/needlez/.compiz/plugins/libanaglyph.so
install   : /home/needlez/.compiz/metadata/anaglyph.xml
install   : build/compiz-anaglyph.schema
Installing icon for anaglyph..
[http://:](http://:) Invalid host name.
Password may be required to install plugin-anaglyph.svg to /usr/share/ccsm/icons/hicolor/scalable/apps

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
Installed plugin-anaglyph.svg to /usr/share/ccsm/icons/hicolor/scalable/apps

---

### Post by soad6 on 2010-11-28
[COLOR=Red][B]DISREGARD THIS POST!! FIXED!!
[/B][/COLOR]
Getting this issue now please any help would be appreciated. thank you.

What would you like to do for screensaver? i/s/u/a/q: i
Initialized empty Git repository in /home/needlez/src/compiz/plugins/screensaver/.git/
remote: Counting objects: 209, done.
remote: Compressing objects: 100% (204/204), done.
remote: Total 209 (delta 119), reused 0 (delta 0)
Receiving objects: 100% (209/209), 54.97 KiB, done.
Resolving deltas: 100% (119/119), done.
Branch compiz-0.8 set up to track remote branch compiz-0.8 from origin.
Building screensaver..
removing  : ./build
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : vector.cpp -> build/vector.lo
compiling : wrapper.cpp -> build/wrapper.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : effect.cpp -> build/effect.lo
compiling : matrix.cpp -> build/matrix.lo
compiling : screensaver.cpp -> build/screensaver.lo
compiling : build/screensaver_options.c -> build/screensaver_options.lo
linking   : build/libscreensaver.la
Installing..
install   : /home/needlez/.compiz/plugins/libscreensaver.soinstall: cannot create regular file `/home/needlez/.compiz/plugins/libscreensaver.so': Permission denied
make: *** [install] Error 1

---

### Post by soad6 on 2010-11-29
[B][COLOR="Blue"]INSTRUCTIONS FOR GETTING JOHNNYG713 SCRIPT TO WORK IF YOU DONT SEE ANY PLUGINS AFTER REBOOT![/COLOR]

ADDED SCRIPT FILE FROM JOHNNYG713 TO MY POST TO MAKE IT EASIER TO FIND![/B]

[COLOR="Blue"]Ok so after going a little insane and almost out of my mind I figured out a solution to getting this to work. Talk about not pretty either. FIRSTLY REINSTALL COMPIZ!! then download the script that JOHNNYG713 has. Run it and when it says that it fails don't worry just go through and (i) install all the plugins you want. then once it says that its done. DO NOT REBOOT! go to home/src/compiz and copy the files folders in there. Make a new folder in home called compiz paste those files into there. Then load up terminal cd to home/compiz/folder ( folder being the folder of the plugin you want) and type make && sudo make install. Do this for each plugin you want then killall compiz. Then compiz --replace &. This will work for ubuntu 10.10 and compiz 0.8.6 with all plugins. Thanx for the help JOHNNYG713 without you I would still be lost at trying to compile from Git![/COLOR]

---

### Post by soad6 on 2010-11-29
Any questions please msg me about it [email]needlez6@aol.com[/email] or same @yahoo.com... peace

---

