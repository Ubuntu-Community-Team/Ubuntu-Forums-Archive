---
title: "GIMP plug-in"
date: 2014-06-20
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2014-06-20
Hello!

Usually insalling plugins so far has been pretty straightforward, but  i'm really having trouble installing InsaneBump on linux and windows.

Is anyone familiar with the plugin and managed to get it working?
If so, i need help, especially for linux version. I have no idea where to put the files.

I have a .zip file InsaneBump version 2.5 containing following files:

fontlucida.png
InsaneBump
interface.png
rocks.jpg
sky.jpg
suppourt.dll
test.b3d

The windows version of this plugin also has Irrlicht.dll file that goes  into the bin directory in Gimp. Linux version of that zip file doesn't  have it.

Now, the InsaneBump is supposed to go to /usr/lib/gimp/2.0/plug-ins folder.

But the plugin doesn't load. It opens a window that's bugged and i can't see what's on it.
Where do the other files go?

In windows version i placed the files in every folder i could imagine,  but when GIMP loads it just opens up a console saying can't load file  <rocks> or the other files...

How do i install this plugin? I searched everywhere and i can't get any  documentation or install notes anywhere, and it's driving me crazy.

Also, are there any other normalmap/specular/other generators for gimp? Linux specifically? If InsaneBump doesn't work.

What am i supposed to do? How do i install it? Where do i put all other files? If someone has some experience with this plugin i'd apreciate the help.
I posted this on the GIMP forums but so far no one has replied. I thought i might have some luck here.

If this is the wrong section i appologise, maybe a moderator can move it to an appropriate section...
Thanks!

EDIT:

Here are the screenshots from the windows console since the ubuntu console thing assumes whatever the bacground i have, and the window shows nothing, but i guess it's the same thing there.
[IMG]http://i57.tinypic.com/2ziwxzp.png[/IMG]
[IMG]http://i58.tinypic.com/20kc46o.png[/IMG]

---

### Post by gordan-vrbanec-vepar on 2014-07-07
Can anyone help me please?

---

### Post by Bucky Ball on 2014-07-07
*Thread moved to **General Help**.*

This might help get things moving. ***Installations & Upgrades*** is for installations and upgrades of the OS. ;)

---

### Post by steeldriver on 2014-07-07
Where did you get it? are you sure it's compatible with your version of gimp? the version in the gimp plugins registry seems to be 1.06

BTW why are you showing us stuff from Windows? how is that relevant?

---

### Post by Bucky Ball on 2014-07-07
> **steeldriver said:**
> BTW why are you showing us stuff from Windows? how is that relevant?

^^^
This. Good pick up. Please boot into Ubuntu, open a terminal and edit the preferences so you have white text/black background.

Could you please also attach images by 'Go Advanced' or 'Adv Reply' and use the paperclip icon. Thanks. ;)

PS: Insane Bump looks like an .exe file. That ain't gonna run in Linux. That's about as far as you'll go (unless you are running Windows Gimp in a virtual machine or Wine, which would be a bit pointless). Looks like a Gimp plugin for Windows, not Linux.

In the top border or your Win console in the second frame of your pic it clearly states, 'InsaneBump.exe'.

---

### Post by Rob Sayer on 2014-07-07
As mentioned, a .exe file isn't going to be any help in linux.  Neither is a .dll file unless it's for windows, and, as also mentioned, running gimp in a windows vm linux session is kind of silly.

There seem to be a number of gimp forums.  If you haven't got a response in one search some others.

On a quick search that doesn't seem to be a well supported plugin.

---

### Post by deadflowr on 2014-07-07
> Here are the screenshots from the windows console since the ubuntu  console thing assumes whatever the bacground i have, and the window  shows nothing, but i guess it's the same thing there.

I don't know what this really means, but perhaps the console window needs to be reset to something viable like solid color.
Look in console menu list edit > profile preferences > background and see about changing that to solid color or custom image.

Anyway, though there is no need to post an image at all, simply copy and paste the terminal output.
Using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"), I might add.

---

### Post by gordan-vrbanec-vepar on 2014-07-08
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

This might help get things moving. ***Installations & Upgrades*** is for installations and upgrades of the OS. ;)

Did it ever! I thought i posted it in Multimedia, but anyway, thank you!

Anyway, i got the plugin here:

[http://blenderartists.org/forum/showthread.php?317041-Insane-Bump-2-0-overhauled-Crazy-bump-alternative](http://blenderartists.org/forum/showthread.php?317041-Insane-Bump-2-0-overhauled-Crazy-bump-alternative)
(there's a 2.5 version on page 2 or 3 of the thread)

And the script here: [http://registry.gimp.org/node/28117](http://registry.gimp.org/node/28117)

I have both the linux and windows versions. Insane bump version 2.5 ...

> **steeldriver said:**
> Where did you get it? are you sure it's  compatible with your version of gimp? the version in the gimp plugins  registry seems to be 1.06

BTW why are you showing us stuff from Windows? how is that relevant?

I'm showing you the windows console output because linux doesn't output anything, like i explained. It pops up a window (not terminal, just normal window), which is blank, then blends in with the backdround. As you move it the background is copied on it and moves with it... IDK how to explain it better. But it seems to be the same issue so i gave you the only output i had. (the issue being, it loads the plugin but can't load other files - font, rocks and others)...

> **Rob Sayer said:**
> As mentioned, a .exe file isn't going to be  any help in linux.  Neither is a .dll file unless it's for windows, and,  as also mentioned, running gimp in a windows vm linux session is kind  of silly.

There seem to be a number of gimp forums.  If you haven't got a response in one search some others.

On a quick search that doesn't seem to be a well supported plugin.

I know that. I have a linux version of this plugin too... It's just that i used the screenshot of the windows console because that's the only one that gave me any output...

> **deadflowr said:**
> I don't know what this really means, but  perhaps the console window needs to be reset to something viable like  solid color.
Look in console menu list edit > profile preferences > background  and see about changing that to solid color or custom image.

Anyway, though there is no need to post an image at all, simply copy and paste the terminal output.
Using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"), I might add.

I wanted to, but as soon as the console appears, it goes semi-white (not responding) and i can't copy/paste it. Just screenshot... Sorry... :(

Anyway, here is a link to the linux version of the plugin if someone wants to give it a go:
[https://www.dropbox.com/s/9qlwkc3hlu6z580/InsaneBump2_5_linux.zip](https://www.dropbox.com/s/9qlwkc3hlu6z580/InsaneBump2_5_linux.zip)

I searched too and it really seems that the plugin isn't all that well supported. 
So if this endeavour fails, can someone recommend a good normal map generator for gimp? Or maybe standalone? For linux...

Thx for replying all! :)

---

### Post by steeldriver on 2014-07-08
Are you sure it's a gimp plugin? it appears to be a standalone 32-bit ELF executable - I was able to run it by unzipping the archive in an arbitrary directory and then doing
```

$ ./InsaneBump 

```
i.e.
```

$ ./InsaneBump 
Irrlicht Engine version 1.8.0
Linux 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:55:18 UTC 2014 i686
Using renderer: OpenGL 3.3.0
Quadro FX 570M/PCIe/SSE2: NVIDIA Corporation
OpenGL driver version is 1.2 or better.
GLSL version: 3.3
Loaded texture: /home/steeldriver/Documents/forums/interface.png
Loaded texture: /home/steeldriver/Documents/forums/rocks.jpg
Could not open file of texture: Untitled
B3dMeshLoader: Warning, different meshbuffers linking to the same vertex, this will cause problems with animated meshes
Loaded mesh: ./test.b3d
Loaded texture: /home/steeldriver/Documents/forums/sky.jpg
Quit message received.

```

[ATTACH=CONFIG]254576[/ATTACH]

---

### Post by gordan-vrbanec-vepar on 2014-07-10
Sorry for the late reply...

Well it says it's a gimp plugin. And gimp seems to want to load it, but then that happens...

But i haven't tried to run it like that. :confused:
Never crossed my mind. Then maybe it's meant to be run separately.
Thanks! I'll try that!

---

