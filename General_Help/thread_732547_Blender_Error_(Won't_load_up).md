---
title: "Blender Error (Won't load up)"
date: 2008-03-23
forum: General Help
---

### Post by CD27 on 2008-03-23
I'm trying to open my blender program, but it keeps closing out. I set it to open in terminal so maybe i could see the errors given out, but they were going to fast that had to take a screen shot so i could see them, here's what it says:

```
guessing 'blender-bin' == ' /usr/bin/blender-bin'
compiled with python version 2.5.1.
checking for installed python....got it!
ignoring xlib error: error code 158 request code 146
ignoring xlib error: error code 158 request code 146
```

and it crashes completely.

Any idea what this means?

I might have a clue though, i ran in terminal not long ago "sudo aptitude install" and i noticed that it was saying "remove" instead of "install" on a few things, could this be linked? maybe not, but just curious.

I uninstalled and reinstalled blender completely and installed everything else that came when i did the search for blender in synaptic. still, however, it won't work, same error code. i've seen a few more of these same crashes on the forum, but no solutions yet...

---

### Post by CD27 on 2008-03-23
Hello? why does it always take me having to just about beg for help for someone to actuall post back? Anyone want to give a hand please?

---

### Post by CD27 on 2008-03-23
I kind of need tis help ASAP b/c this program is required for my job

---

### Post by CD27 on 2008-03-23
you know what, just screw it, i'll figure it out myself. thanks for help guys.

---

### Post by pPrdrm on 2008-03-23
Hello there CD27,
I know that it's very hard when you just want to do your job and the only program you can use is not working, but don't take it out to other people like they have something against you or they don't want to help you. From what I see, 20 people read your post but they just didn't have any answer for you. They are not all programmers or computer experts. If you could tell us more about your situation maybe someone could help you, like what version of blender are you using, is it the one from the repositories or from the official blender site, did you upgrade your system or what version of ubuntu you are running?

---

### Post by CD27 on 2008-03-23
It's the repository one (i can't figure out how to install the one from the site).
I use Gutsy
It's version 2.5 (hence python 2.5.1)

and it's giving me the code above.

I don't expect everyone to know how to help, I expect some kind of response. I know there are hundreds of people on, becuase my post keeps moving down and to a completely different page in just one hour. so i have to keep booting it back up or no one will see it. Yes, it is annoying when i can't do my job b/c my program doesn't work.

---

### Post by pPrdrm on 2008-03-23
I used to have that same message when I was running Feisty but that didn't stop blender from starting. I think that this error would prevent some futures of blender to run but not blender it self. Anyway it disappeared when I moved to Gutsy. Try to run the version from the official blender site. Just unpack the compressed file to a location of your preference and run it using this command: **/home/Username/BlenderFolder/blender -w -p 0 0 1270 945**. The last two numbers are for the size of the window that blender will open. Also if you use Compiz try to disable it. And check if your graphic card is working properly.

---

### Post by CD27 on 2008-03-23
it still won't load :( i don't know what to do really. It seems that it maxes out my ram and just crashes instantly. cuz when i look at the system processes, it shos a single spike when i open it.

---

### Post by Darxus on 2008-05-06
I'm having a similar problem.

Start blender (works fine).  Click add / mesh / UVsphere / OK.  Then when I hit tab:

$ blender &
[1] 6872
$ guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Ignoring Xlib error: error code 158 request code 146
Ignoring Xlib error: error code 158 request code 146
Segmentation fault (core dumped)

I'm running an up to date gutsy (just did an aptitude dist-upgrade and reboot to verify).  
I am using the blender package from the ubuntu archives.
Version: 2.44-2ubuntu2

X Window System Version 1.3.0
(**) |   |-->Device "ATI Technologies, Inc. Radeon RV200 QW [Radeon 7500]"
        Driver          "ati"

[http://www.chaosreigns.com/blender/xorg.conf](http://www.chaosreigns.com/blender/xorg.conf)
[http://www.chaosreigns.com/blender/Xorg.0.log](http://www.chaosreigns.com/blender/Xorg.0.log)

---

### Post by Darxus on 2008-05-06
Grabbed: [http://download.blender.org/release/Blender2.45/blender-2.45-linux-glibc236-py25-i386.tar.bz2](http://download.blender.org/release/Blender2.45/blender-2.45-linux-glibc236-py25-i386.tar.bz2)

cd ~/dl/blender-2.45-linux-glibc236-py25-i386
$ ./blender 

Exact same procedure as I did above:

darxus@darxus-desktop:~/dl/blender-2.45-linux-glibc236-py25-i386$ ./blender 
guessing './blender' == '/home/darxus/dl/blender-2.45-linux-glibc236-py25-i386/./blender'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Ignoring Xlib error: error code 158 request code 146
Ignoring Xlib error: error code 158 request code 146
Segmentation fault (core dumped)

Hey look, a debug option.  Same again:


$ ./blender -d
guessing './blender' == '/home/darxus/dl/blender-2.45-linux-glibc236-py25-i386/./blender'
Blender 2.45 (sub 0) Build
argv[0] = ./blender
argv[1] = -d
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Ignoring Xlib error: error code 158 request code 146
Ignoring Xlib error: error code 158 request code 146
Color depth r 8 g 8 b 8
Aux buffers: 0
read file 
  Version 242 sub 4
read file /home/darxus/.B.blend
  Version 244 sub 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/darxus/.blender/Bpymenus

Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBMesh
 OBCube
 OBLamp
 OBCamera
Segmentation fault (core dumped)


Same results with pPrdrm's recommended ./blender -w -p 0 0 1270 945

Kernel is:  
Linux darxus-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by Darxus on 2008-05-06
"$ mv .B.blend .B.blend.0" didn't change anything.

---

### Post by Darxus on 2008-05-06
In searching for the meaning of the error:
"Ignoring Xlib error: error code 158 request code 146"
I came across 

"$ glest X Error of failed request: BadLength (poly request too large or internal Xlib length error) Major opcode of failed request: 146 (NV-GLX) Minor opcode of failed request: 3 () Serial number of failed request: 8 Current serial number in output stream: 8" - [http://www.happypenguin.org/show?Glest&start=60](http://www.happypenguin.org/show?Glest&start=60)

I didn't expect it to be related, but noted the "poly request too large" part and tried reducing the poly count I was working with.  I had also noticed less complicated meshes (cubes) weren't having this error.

Start blender, add / mesh / UVsphere / reduce Segments and Rings from 32 to 16 / OK.  Then when I hit tab it doesn't crash (which is where it was crashing before).

I repeated the process again with the default 32 Segments and Rings and it crashed again as expected.

From /proc/cpuinifo:
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz

Debug output with the reduced segments and rings which didn't crash, and then I quit blender:

$ blender -d
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.44 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Ignoring Xlib error: error code 158 request code 146
Ignoring Xlib error: error code 158 request code 146
Color depth r 8 g 8 b 8
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
/home/darxus/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBMesh
 OBCube
 OBLamp
 OBCamera
Saved session recovery to /home/darxus/.blender/quit.blend

Blender quit

---

### Post by threegremlins on 2008-05-15
I'm getting a different error from blender. launching from a terminal the next line after "got it" says illegal instruction. at the same time the window opens and immediately shuts down. Some history first, I downloaded a pre-release of hardy and after awhile it started acting buggy, blender was working fine. I switched to Xubuntu hardy official release and didn't care for it plus blender wouldn't work after installing the updates. I switched back to Ubuntu installing the official release this time, installed the updates and then instaloling bender it didn't work.  After getting my wacom pen working I tried tweaking my nvidia card and lost main use of the wackem pen. I threw up my hands and reinstalled Ubuntu official release but before installing upgrades I installed blender and it worked fine, after updating, there were 67 files, it didn't work. somehow one or a few of those 67 files apperently don't work with blender and as far as I can tell from perusing Search>Blender in the forum there are a number of other 3d programs like wings 3d for example not running properly. I do hope there are enough bug reports sent in that it gets acted upon quickly.

---

### Post by ROBarber on 2008-05-20
try to install libgl1-mesa-swx11. at least for me solved this error.

apt-get install libgl1-mesa-swx11

and start again blender

---

### Post by threegremlins on 2008-06-04
Googling the same with problem blender yet again I came across this thread from way back.
I tried 
apt-get install libgl1-mesa-swx11
and blender is working again yaaaaa I'm a happy camper
Thanks ROBarber

---

