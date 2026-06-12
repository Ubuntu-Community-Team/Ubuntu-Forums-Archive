---
title: "xrandr commands do nothing"
date: 2016-05-07
forum: General Help
---

### Post by CaptainMark on 2016-05-07
I was lead to believe that xrandr commands should make immediate changes to your user session but I can't get them to work. I'm trying to manually change the DPI of each of my monitors

Monitor 1 is called DP2 has a resolution of 1920x1080 (landscape) it's my primary monitor and a physical dpi of 81x81
Monitor 2 is called HDMI1 has a resolution of 1080x1920 (portrait) and has a physical dpi of 102x102 and is positioned to the left of the primary monitor

Because of the incorrect dpi settings the cursor jumps when moving from one monitor to the next so I'm trying to change them, also the login window second monitor is on its side and needs to be rotated, which I understand can be corrected by issuing xrandr commands to the login manager if only I could get the commands to work. My issue is that xrandr commands have no effect, perhaps I'm doing it wrong. Ill paste my terminal output below so you can see what I tried, towards the end I got desperate and just tried rotating one screen entirely but it still does nothing.

Some help would be appreciated

```

[18:30:33] mark@desktop ~ $ xrandr
Screen 0: minimum 320 x 200, current 3000 x 1969, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1080x1920+0+0 right (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 connected primary 1920x1080+1080+889 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      60.0*+   50.0     59.9  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1280x720       60.0     50.0     59.9  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
[18:47:23] mark@desktop ~ $ xrandr --output HDMI1 --dpi 102
[18:47:50] mark@desktop ~ $ xrandr --output HDMI1 --dpi 96
[18:48:02] mark@desktop ~ $ xrandr --output HDMI1 --dpi 102
[18:48:15] mark@desktop ~ $ xrandr --output DP2 --dpi 81
[18:49:19] mark@desktop ~ $ xrandr --output HDMI1 --rotate right

```

---

### Post by ajgreeny on 2016-05-07
The command **xrandr** does exactly what you see; it prints out information but changes nothing.

Use command **man xrandr** to see all that it can do if you use the appropriate options.
The ones you want are probably these from **man xrandr** as I mention above.

```
 These  options  are  available  for  X servers supporting RandR version 1.1 or older. They are still valid for
       newer X servers, but they don't interact sensibly with version 1.2 options on the same command line.

       -s, --size size-index or --size widthxheight
              This sets the screen size, either matching by size or using the index into the list of available sizes.

       -r, --rate, --refresh rate
              This sets the refresh rate closest to the specified value.

```

---

### Post by CaptainMark on 2016-05-07
Not even sure you read my post or not all the way through. I have tried xrandr command with several options, I figured out the rotate option isn't working because it's already rotated onto its right side, this is relative to the upright not its current orientation so I can't rotate right again. I don't need to set the resolution as the two screens are the same resolution thats what the size is for but the dpi option has no effect. In reality the two screens are the same resolution but one is much larger that the other so the border between the two monitors may cover 1080 pixels on the right screen but would be say 1200 pixels on the other but the system just thinks its 1080 pixels on both monitors. They have different dpi but changing the dpi doesn't change anything

---

### Post by sudodus on 2016-05-07
I'm not sure that --dpi works as you expect, it might change the screen 'size in mm', not the pixel resolution. I guess you can use the best fitting pixel resolution (the -s alias --size option).

Have you tried the options --panning, --transform,  ..., --fb ?

```
      --panning  widthxheight[+x+y[/track_widthxtrack_height+track_x+track_y[/border_left/border_top/border_right/border_bot&#8208;
       tom]]]
              This option sets the panning parameters.  As soon as panning is enabled, the CRTC position can change with every
              pointer move.  The first four parameters specify the total panning area, the next four the pointer tracking area
              (which defaults to the same area). The last four parameters specify the border and default  to  0.  A  width  or
              height  set  to zero disables panning on the according axis. You typically have to set the screen size with --fb
              simultaneously.

       --transform a,b,c,d,e,f,g,h,i
              Specifies a transformation matrix to apply on the output. Automatically a  bilinear  filter  is  selected.   The
              mathematical form corresponds to:
                     a b c
                     d e f
                     g h i
              The  transformation  is  based  on  homogeneous coordinates. The matrix multiplied by the coordinate vector of a
              pixel of the output gives the transformed coordinate vector of a pixel in the graphic buffer.   More  precisely,
              the  vector (x y) of the output pixel is extended to 3 values (x y w), with 1 as the w coordinate and multiplied
              against the matrix. The final device coordinates of the pixel are then calculated with the  so-called  homogenic
              division  by  the  transformed  w coordinate.  In other words, the device coordinates (x' y') of the transformed
              pixel are:
                     x' = (ax + by + c) / w'   and
                     y' = (dx + ey + f) / w'   ,
                     with  w' = (gx + hy + i)  .
              Typically, a and e corresponds to the scaling on the X and Y axes, c and f corresponds  to  the  translation  on
              those  axes,  and  g,  h, and i are respectively 0, 0 and 1. The matrix can also be used to express more complex
              transformations such as keystone correction, or rotation.  For a rotation of an angle T,  this  formula  can  be
              used:
                     cos T  -sin T   0
                     sin T   cos T   0
                      0       0      1
              As a special argument, instead of passing a matrix, one can pass the string none, in which case the default val&#8208;
              ues are used (a unit matrix without filter).

       --scale xxy
              Changes the dimensions of the output picture. Values superior to 1 will lead  to  a  compressed  screen  (screen
              dimension  bigger  than  the dimension of the output mode), and values below 1 leads to a zoom in on the output.
              This option is actually a shortcut version of the --transform option.

       --scale-from wxh
              Specifies the size in pixels of the area of the framebuffer to be displayed on  this  output.   This  option  is
              actually a shortcut version of the --transform option.

       --primary
              Set the output as primary.  It will be sorted first in Xinerama and RANDR geometry requests.

...

       --prop, --properties
              This option causes xrandr to display the contents of properties for each output. --verbose also enables --prop.

       --fb widthxheight
              Reconfigures  the  screen  to  the  specified size. All configured monitors must fit within this size. When this
              option is not provided, xrandr computes the smallest screen size that will hold the set of  configured  outputs;
              this option provides a way to override that behaviour.
```

---

### Post by ajgreeny on 2016-05-07
It would have helped us if you had shown us what commands you had already used, as I had no idea what you had tried, hence my post above.

The only command you show is the simple **xrandr** with no options.

---

### Post by CaptainMark on 2016-05-10
Sorry but check again, there's 5 xrandr commands there, you must have skim read it.

Anyway I've done some digging and the DPI command does work in xrandr but it has no visible difference on the monitor, after some digging I've realized the problem I've been having isn't caused by the DPI setting, the desktop draws windows as say 200 pixels high by 200 pixels wide so a window placed on the border will appear different sizes in both monitors unless the monitors are the same physical size and resolution.  The answer is to use the scale command and scale the smaller monitor by a ratio of physical sizes of my two monitors, (477mm / 598mm = 0.7976) and then to change the co-ordinates slightly so everything lines up. This way a square window placed across the border will appear square and lined up correctly, rather than bigger and smaller on opposing monitors, the trade off is that my smaller monitor is not able to utilise it's full resolution and is effectively running at a lower resolution.

---

### Post by sudodus on 2016-05-10
Congratulations and thanks for sharing :KS

If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

