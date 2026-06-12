---
title: "Blender3D Crashes!"
date: 2005-06-04
forum: General Help
---

### Post by GandalfX86 on 2005-06-04
Im new to Ubuntu and I wanted to use Blender 3D. I loaded the Package with Synaptic and tried to run Blender. It works fine until I want to open any menu (by pressing space eg.), because then Blender stops to do anything for about 1 Minute. and then a Black Box (which has the size) of the menu opens. 

I have already installed Python 2.3 and the Python Dev-Package but it still does not work. 

I use a nVidia 6600GT with the newest driver (1.0-7174)

---

### Post by tikal26 on 2005-06-07
Did it use to work with the older drivers, I had some problems with the new drivers so i just went back. I don't know if that is of any help

---

### Post by Offoffoff on 2007-11-05
Your problem is not problem, man. I can not even start Blender. I am thinking it is due my Compiz-Fusion, but I do not like to switch off effects.
This is the debug log:
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.44 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Color depth r 5 g 6 b 5
Aux buffers: 0
read file 
  Version 242 sub 4
read file 
  Version 241 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/alien/.blender/Bpymenus

Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Color depth r 5 g 6 b 5
Aux buffers: 0
Segmentation fault (core dumped)

---

### Post by saxofoner on 2007-11-07
@ O. P. :  Try downloading the latest build for your architecture from one of the big blender sites, like [http://www.graphicall.org/builds/index.php](http://www.graphicall.org/builds/index.php) . 
If you get it from blender.org, MAKE SURE you choose "Dynamic."  

Also, what drivers are you using?

---

