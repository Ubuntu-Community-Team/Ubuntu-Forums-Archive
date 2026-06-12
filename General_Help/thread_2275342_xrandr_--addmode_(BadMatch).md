---
title: "xrandr --addmode (BadMatch)"
date: 2015-04-25
forum: General Help
---

### Post by jeanmarat on 2015-04-25
I have an LG monitor* Lg Ws2243s* that gives a 1920x1080 resolution.

After doing a gtf 1920 1080 60

and xrandr --newmode 

Xrandr gives out :


```
VGA-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 

    1024x768       60.0 + 
    1360x768       60.0     59.8   
    1152x864       60.0*  
    800x600        72.2     60.3     56.2   
    680x384        60.0     59.8   
    640x480        59.9   
    512x384        60.0   

    400x300        72.2   
    320x240        60.1   
 DVI-I-1 disconnected (normal left inverted right x axis y axis) 
 HDMI-0 disconnected (normal left inverted right x axis y axis) 
   1920x1080_60.00 (0x2b0)  172.8MHz 
         h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz 
         v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz 
   19201080 (0x2b2)  172.8MHz 
         h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz 
         v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz

```


 

 xrandr --addmode VGA-0 1920x1080_60.00 

 

 gives :
 ```
X Error of failed request:  BadMatch (invalid parameter attributes) 

   Major opcode of failed request:  140 (RANDR) 
   Minor opcode of failed request:  18 (RRAddOutputMode) 
   Serial number of failed request:  29 
   Current serial number in output stream:  30 

``` 

 xrandr --addmode VGA-0 19201080
 gives the same
 

 what is the problem ?

thanks in advance

---

### Post by nerdtron on 2015-04-25
I had a similar problem before. Post number 3 in this link help me: [http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186)

---

### Post by jeanmarat on 2015-04-25
As I already mentioned i get badname 

xrandr | grep maximum 

 ```


 Screen 0: minimum 8 x 8, current 1152 x 864, maximum 16384 x 16384 

``` 

 gtf 1920 1080 60.00 
```


  
   # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz 

   Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync 

``` 

 xrandr --newmode "1920x1080_60.00" 172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync  


 > X Error of failed request:  BadName (named color or font does not exist) 

   Major opcode of failed request:  140 (RANDR) 
   Minor opcode of failed request:  16 (RRCreateMode) 
   Serial number of failed request:  29 
   Current serial number in output stream:  29 



---

### Post by matt_symes on 2015-04-25
Hi

> **jeanmarat said:**
> 
X Error of failed request:  BadName (named color or font does not exist) 

   Major opcode of failed request:  140 (RANDR) 
   Minor opcode of failed request:  16 (RRCreateMode) 
   Serial number of failed request:  29 
   Current serial number in output stream:  29

The above error suggests it may need the high dpi fonts.

```
sudo apt-get install xfonts-100dpi xfonts-75dpi
```

They are not installed by default (at least on my 14.04 installation)

```
matthew-laptop:/home/matthew:1 % dpkg -l | egrep "xfonts-100dpi|xfonts-75dpi"
matthew-laptop:/home/matthew:1 %
```

After running the above command, reboot and try to create the new mode again.

BTW: I've always used cvt and not the older gtf.

Kind regards

---

### Post by jeanmarat on 2015-04-25
No luck with the fonts.

By the way which driver should I have running while doing this modifications ?

X.org ?

---

### Post by matt_symes on 2015-04-25
Hi

> **jeanmarat said:**
> No luck with the fonts.

Hmm. That's a shame.

BTW: It would be so useful if you posted all the output from the terminal. You have said it fails but it does not specify where it failed, how it failed, the exact commands you typed in, the exact order and the messages returned.

> By the way which driver should I have running while doing this modifications ?

X.org ?

Xorg is a display server more than a graphics driver.

I have had a problem where i could not get a sis graphics card to display the correct resolution using xrandr but i got it working using a custom xorg.conf file. Maybe that will work for you but first let's see if anybody else, with a setup similar to yours, can help you first.

Post the output of this command to display your graphics cards and the current driver.

```
lspci -nnk | grep -iA2 vga
```

Kind regads

---

### Post by jeanmarat on 2015-04-26
lspci -nnk | grep -iA2 vga


```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 620] [10de:0f01] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:3547]
    Kernel driver in use: nouveau
```

---

### Post by jeanmarat on 2015-04-26
In additional drivers I have installed :

   Nvidia  driver 340.76  
 331.113
 304.125
 349.16
 346.59
 331.113
 304.125


Nvidia suggests 346.59 , I picked that one but no 1920x1080 option for my LG monitor that outputs that kind of resolution

---

### Post by jeanmarat on 2015-04-26
This guy has the same monitor with me :

post #9 

[http://ubuntuforums.org/showthread.php?t=1946208](http://ubuntuforums.org/showthread.php?t=1946208)

how do i install EDID and xorg.conf. that he provides ?

---

### Post by jeanmarat on 2015-04-26
Strangely I can get 1600x900 but not 1920x1080

this worked :


    Cvt 1600 900 60 

 ```


 # 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz 
 Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync 

 


```

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync 
 

 xrandr --addmode VGA-1 1600x900_60.00

---

### Post by jeanmarat on 2015-04-26
Ok this seems weird !
 

 After installing bummlebee (don't know if that had to do with it) and switching to one random Nvidia Driver 304.125 from NVIDIA-304-updates propriety
 

 I entered this in my console :
 

 cvt 1920 1080 60 
 # 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz 
 Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync 
 

  xrandr --newmode  "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync 
 

 xrandr --addmode VGA-1 1920x1080_60. 
 

 It works

---

### Post by jeanmarat on 2015-04-26
After rebooting besides losing my xrandr resolutions settings trying all over again to enter either a 1600 x 900 or a 1920 1080 resolution i get this thing :


**xrandr: Failed to get size of gamma for output default**

---

### Post by jeanmarat on 2015-06-16
This is the output for inxi -G
> inxi -G
Graphics:  Card: NVIDIA GF108 [GeForce GT 620] 
           X.Org: 1.16.0 drivers: fbdev (unloaded: vesa) FAILED: nouveau Resolution: 1024x768@76.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits) GLX Version: 3.0 Mesa 10.3.2


---

### Post by notte on 2015-12-02
```
X Error of failed request: BadName (named color or font does not exist) 

``` 

I had the same problem. Then I changed the name of xrandr --newmode from "1600x1200@75.00" to "1600x1200-75.00" and it was created without errors. Trying again with the same name returns the same error message. 
My idea is that the command accepts only the first time one new mode generation...

---

