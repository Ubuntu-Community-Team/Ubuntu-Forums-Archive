---
title: "Compiz fusion 0.7.6"
date: 2008-06-30
forum: General Help
---

### Post by bijeeshvs on 2008-06-30
hello guys can anyone say how to install/upgrade Compiz fusion 0.7.6 ? can we play it safe through synaptic or is there any safer methods as i dont want to end up in a crashed desktop,

if any one used it please let me/us know how is it all going............

---

### Post by aashay on 2008-06-30
Get it from the following repos:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
Works fine for me. No crashes at all.

---

### Post by bijeeshvs on 2008-06-30
> **aashay said:**
> Get it from the following repos:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
Works fine for me. No crashes at all.

thanks a lot buddy its just working fine...................

---

### Post by Teonline on 2008-06-30
Sry, i am a little noob, just passed from windows, how to install compiz from these links? thx alot

---

### Post by bijeeshvs on 2008-06-30
Ok dont worry

1, go to "system=> administration=> software sources" 
2, select the "third party software" TAB
3, click on the "Add" button and add the following lines one by one

[IMG]http://img3.orkut.com/images/milieu/1207383420/1214856025809/48872601/ln/Zeyqw3v.jpg?sig=1uhkicz[/IMG]

```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```
```
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```
4. Then close the "software sources" by clicking on the close button
5, system will ask you to reload the package information , choose to reload
6, open "system=> administration=> update manager "
compiz and components must be listed there by now select to install and thats it u are done
if u run into any trouble in the procedure plese come back............

---

### Post by Teonline on 2008-06-30
Ok it worked fine ;) Now if i run compiz from terminal i got an error:
"Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
"

Is there any icon i have to click or is a normal error? With Gutsy i was using Gnome compiz and it worked fine, i still have it installed in synaptic but i cant find anymore its icon :S  Any tips? :) thx alot

---

### Post by bijeeshvs on 2008-06-30
do you have nvidia or ati graphics card?
if you have one , do you have the drivers installed properly?
for settings of compiz go to "system=> preferences=> compiz config settings manager"
if its not there , go to "system=> administration=> synaptic package manager" and search for compizconfig and install the above mentioned app
then u can use it from menu or by typing "ccsm" in a terminal............

---

### Post by Cole on 2008-06-30
When I attempt to install this using those repositories from launchpad (@ 64bit Hardy Heron), compiz will run for a second or two, then will crash while reading .so files from /usr/lib/compiz.

---

### Post by bijeeshvs on 2008-07-01
> **Cole said:**
> When I attempt to install this using those repositories from launchpad (@ 64bit Hardy Heron), compiz will run for a second or two, then will crash while reading .so files from /usr/lib/compiz.

its just working fine for me, 
try one thing run compiz from a terminal and see what error is happening....

---

### Post by Cole on 2008-07-01
> **bijeeshvs said:**
> its just working fine for me, 
try one thing run compiz from a terminal and see what error is happening....

I found that one of the extra plugins I compiled from source on 0.7.4 was causing the entire system to crash.  Uninstalled it and now it works like a charm. :)

---

### Post by Teonline on 2008-07-02
I installed compiz from package manager and all worked, it was really cool, i put loads of effects and so on, all worked fine, then i restarted pc and when i try to rotate cube system crashed. To let the sistem speed up i had to turn off al the new features :S Any tips?

---

### Post by bijeeshvs on 2008-07-02
> **Teonline said:**
> I installed compiz from package manager and all worked, it was really cool, i put loads of effects and so on, all worked fine, then i restarted pc and when i try to rotate cube system crashed. To let the sistem speed up i had to turn off al the new features :S Any tips?

hello teonline dont worry just go to a terminal (applications => accessories => terminal ) and type " compiz --replace " and watch the window it will spit out some error messages if thats specific to some plugin just disable it 
and also check your system monitor ( system => administration => system monitor ) for cpu usage memory and swap usge and check that if any program is consuming much memory or cpu.................

---

### Post by Teonline on 2008-07-03
Thx a lot for help, here is the log of compiz even with i have no visible problems:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```
Any tips ;)

---

### Post by plamen_todoroff on 2008-07-03
Is this the official compiz developer's repository? What I mean is, is it like the AWN developer's repository in Launchpad?

---

### Post by aashay on 2008-07-03
> **plamen_todoroff said:**
> Is this the official compiz developer's repository? What I mean is, is it like the AWN developer's repository in Launchpad?

I'd frankly direct that question elsewhere. But from what I know, it is **not**

---

### Post by bijeeshvs on 2008-07-05
> **Teonline said:**
> Thx a lot for help, here is the log of compiz even with i have no visible problems:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```
Any tips ;)

hello teoline 
from the output it says that you have no nvidia card if u actually have an nvidia graphics card check that restricted drivers is working if u have not one please tell which card ur using...................

---

### Post by El_Greco on 2008-07-13
Hey all, I just upgraded to fusion 0.7.6 from 0.7.4, and it's been going a little wonky on me. Whenever i wsitch desktops or move windows when they're wobbly, they go all blank on me. also when i use any windows switchers. i tried that "compiz --replace" thing that was mentioned earlier, and i got this:

```
robert@robert-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

I have half of an idea of what some of them mean, notably the last two, but i don't have any idea about the other ones. a little help?

---

### Post by plamen_todoroff on 2008-07-13
I did add this launchpad repo, did all the upgrades after that (all compiz connected) and everything works fine.

I just want to ask is the cube reflection and deformation pludin the only one that is a new one (I've been using the official ubuntu repos till now)?

And I can't seem to find the animation speed setting in the 3d windows plugin after updating from this new repo. Is it gone?

---

### Post by azer89 on 2008-07-14
> **plamen_todoroff said:**
> 

And I can't seem find the animation speed setting in the 3d windows plugin after updating from this new repo. Is it gone?

yep, it's gone...

---

### Post by dyoung on 2008-07-16
> **bijeeshvs said:**
> Ok dont worry

1, go to "system=> administration=> software sources" 
2, select the "third party software" TAB
3, click on the "Add" button and add the following lines one by one

[IMG]http://img3.orkut.com/images/milieu/1207383420/1214856025809/48872601/ln/Zeyqw3v.jpg?sig=1uhkicz[/IMG]

```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```
```
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```
4. Then close the "software sources" by clicking on the close button
5, system will ask you to reload the package information , choose to reload
6, open "system=> administration=> update manager "
compiz and components must be listed there by now select to install and thats it u are done
if u run into any trouble in the procedure plese come back............

When i attempt to go to the update manager i get the following error  'E:Malformed line 56 in source list /ect/apt/source.list (absolute dist) E:The list of sources could not be read  Can you please advise. (i am very new to ubuntu and trying to install the compiz sphere option.) Thanks

---

### Post by parajuito on 2008-07-25
Thank works perfect ^^

---

### Post by pratiks19 on 2008-10-19
There are some problems which i got after installing compiz 0.7.6, i also upgraded all the compiz components whose 0.7.6 upgrade was available
Also i have installed emerald.

problems:
1) window title bar not visible
2) Alt+F2 doesnt start the run, though it is still present in the keyb shortcuts

I get this error when i type "compiz -replace &" in the terminal

[1] 6553
Checking for Xgl: pratik@pratik-laptop:~$ not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Error: Couldn't load plugin '–replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_border_picture
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

plz help

---

### Post by bijeeshvs on 2008-10-21
Is The .7.6 version stable?

try > compiz --replace

i am using .7.4 version and its rock stable and working fine....................

---

### Post by Crimson Fatalis on 2008-11-07
Can anyone help? i get this error when i reload from software sources

Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/mai/binary-i386/Packages.gz](http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/mai/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

and so i could not get update to the compiz 0.7.6, how can i fix this problem?

---

