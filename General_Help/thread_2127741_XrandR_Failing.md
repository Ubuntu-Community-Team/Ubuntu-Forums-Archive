---
title: "XrandR Failing?"
date: 2013-03-21
forum: General Help
---

### Post by MichaelAOlson on 2013-03-21
I'm trying to run Heroes of Newerth on my Ubuntu 12.04 machine and after installing successfully, I click the icon and it doesn't start, the screen goes black for a moment then it goes back to the desktop. After some research I found that I might need additional drivers, sure enough I did. I downloaded and installed those and it still doesn't work. I read that:
[B]
mkdir -p "/home/$(whoami)/.Heroes of Newerth/game"; echo -e "SetSave \"vid_bpp\" \"32\"\nSetSave \"vid_refreshRate\" \"60\"\nSetSave \"vid_resolution\" \"$(xrandr | grep \* | cut -d' ' -f4 | tr x ,)\"\nSetSave \"gl_modesetting\" \"randr,randr11\"" > "/home/$(whoami)/.Heroes of Newerth/game/startup.cfg"[/B]

would solve the problem, but it returned the result:

**xrandr: Failed to get size of gamma for output default**

Then I tried:

**xrandr --output default --mode 1280x1024**

and got the same error. Then I just typed:

**xrandr**

and the nice result was:
[B]
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0     52.0     53.0  
   1280x960       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0     73.0     74.0  
   800x512        75.0  
   720x450        76.0  
   680x384        77.0     78.0  
   640x512        79.0     80.0  
   640x480        81.0     82.0     83.0     84.0  
   576x432        85.0     86.0     87.0     88.0  
   512x384        89.0     90.0     91.0  
   416x312        92.0  
   400x300        93.0     94.0     95.0     96.0  
   320x240        97.0     98.0     99.0  
[/B]
Some additional information, after typing: 

**lspci |grep VGA **

to get my videocar/chip, I get:

**01:00.0 VGA compatible controller: NVIDIA Corporation NV17 [GeForce4 MX 440] (rev a3)**

---

### Post by MichaelAOlson on 2013-03-21
Also, 
Minimum requirements for Heroes of Newerth:
		Processor - 2.2GHz Pentium 4 / AMD 2400+ or faster
		RAM - 1.5GB of RAM
		Video Card - 128MB fully OpenGL 2.0 / GLSL 1.20 compliant Geforce or Radeon
		Network Connection Required

My computer: 
Processor - 2.2GHz Pentium 4
RAM - 1.5GB of RAM
Video Card -  Geforce4 MX 440
Internet Connection is great, Comcast @8MB/s

---

