---
title: "Having issues with my HDMI port to my TV"
date: 2022-02-16
forum: General Help
---

### Post by thejbear on 2022-02-16
Hello, fellow Ubuntu users. Glad to be here. Have loved Ubuntu since 2016. Anyways I'm having a big issue here with my HDMI port on my laptop which is a Lenovo IdeaPad 330. When I plug it in now it just shows the Lubuntu screen like a start up and that is all. Won't show my desktop soni can actually watch my movies and tv, etc. Any help would much be appreciated.

Thanks guys.

---

### Post by MAFoElffen on 2022-02-16
Is this because both screens (internal laptop screen and external monitor) are active at the same time? And that the Laptop screen is already taken up as the primary display and the external as secondary display? Nor that you have both screens setup as Mirrored displays of the same workspace?

Please post the results of 
```

xrandr -q

```
Within CODE TAGs...

---

### Post by thejbear on 2022-02-16
My TV is actually a screen projector that i watch on my wall. Here is the code I got back from the requested terminal command. I also do usual plug it in with both of them on.

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 disconnected (normal left inverted right x axis y axis)


```

Nothing is connected at the moment kinda gave up on it when I couldn't get the SUper Bowl on the wall.

---

### Post by thejbear on 2022-02-16
My TV is actually a screen projector that i watch on my wall. Here is the code I got back from the requested terminal command. I also do usual plug it in with both of them on.

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 disconnected (normal left inverted right x axis y axis)


```

Nothing is connected at the moment kinda gave up on it when I couldn't get the SUper Bowl on the wall. 

Also this is what i get when it is plugged in had the projector off first, then plugged into my laptop.
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 connected (normal left inverted right x axis y axis)
   1360x768      60.37 +
   1920x1080     60.00    50.00    59.94  
   1920x1080i    60.00    60.00    50.00    59.94  
   1280x1024     60.02  
   1280x720      60.61    60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  

```

---

### Post by MAFoElffen on 2022-02-16
If you look at the display settings panel in the attachment, if you have two active displays connected, and turned on, then you have three options: Join Displays, Mirror, and Single Display. Those modes are explained as:

Join Displays: In this display mode the screen edges will be linked and things can pass from one screen to the other one.

Mirror: It will set the same resolution and orientation for both displays and alike content will be shown on both screens.

Single Display: Only one display is set up, effectively shutting down the other.

Choose any of the displays from the the diplay name tabs, then you can also set their resolution, scale or orientation of their screens.

---

### Post by thejbear on 2022-02-17
Thank you very much! I
ve seen those settings before however this is what im getting on lubuntu.. so im a little lost of  where to find it?

[[IMG]https://i.postimg.cc/8jGVQm6m/screen.jpg[/IMG]]("https://postimg.cc/8jGVQm6m")

---

### Post by MAFoElffen on 2022-02-17
Give me a few minutes to spin up a pure Lubuntu 20.04.3 instance and I'll be back....

---

### Post by thejbear on 2022-02-17
> **MAFoElffen said:**
> Give me a few minutes to spin up a pure Lubuntu 20.04.3 instance and I'll be back....


Awesome, youre amazing! Appreciate it..

---

### Post by MAFoElffen on 2022-02-17
Preferences > LXQT Settings > Monitor Settings

Different look to the setting window. Same functionality.

Look in "your" attached Screen Shot from your post, at the Icon in the lower left, named "Monitor Settings".

---

### Post by thejbear on 2022-02-17
Ok, i Went to the monitor and ive been thru all the available tabes as seen on the screen shot below, and i see nothing that allows me to mirror or anything of the sort....

[[img]https://i.postimg.cc/8fvwKKWv/screen2.jpg[/img]](https://postimg.cc/8fvwKKWv)

---

### Post by thejbear on 2022-02-17
No worries fellow ubuntu users, I've decided im switching to Kali which is pretty much based on ubuntu anyways. If that fails I might test out quebes OS(not familiar with fedora), however if all that fails with the hdmi port I will go to regular ubuntu!

I appreciate the help guys.

---

### Post by coffeecat on 2022-02-17
> **thejbear said:**
> I've decided im switching to Kali which is pretty much based on ubuntu anyways.

A few points of information. Kali is **not** based on Ubuntu. Kali is a specialised distro designed for penetration testing and ethical hacking. It seems an odd choice for what you were trying to do with Lubuntu.

---

### Post by MAFoElffen on 2022-02-17
If you look in the panel of the Monitor Settings Window Pane of your screen shot, it only shows the there is only one monitor connected at eDP-1... If you have both Displays connected and on, then the same panel would also show the "HDMI" port, with the TV as taht connected monitor on that HDMI port. That whole Window changes and evolves, depending what is connected/active.

Not completely sure if that, in Lubuntu, is  plug-and-play, or if you have to have the devices connected and on before boot. I am suspecting as the prior, but cannot confirm that. For some "video drivers", it is the later. And on those, if something is defined, but is not on for so long, then it turns that unconnected video port off after that timeout..

---

