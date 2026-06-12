---
title: "Display orientation not changable"
date: 2008-04-23
forum: General Help
---

### Post by jlh68 on 2008-04-23
I am using 8.04-Beta, and I have a new 22-inch wide screen monitor.  The monitor is made so that the screen can be rotated from the horizontal to the vertical position (Some might call that Landscape to Portrait, but I don't know why?).  When I go to the [screen resolution] pull down menu, the choice is not there for changing the orientation.  On my laptop using 7.10 I do have the choice and no reason to use it.

My question is:  Is the problem in the OS or the Monitor?  Or what do I need to do to access that feature?  I would like to use it as most documents are longer than they are wide.

---

### Post by ryanhaigh on 2008-04-24
I would guess that this is a feature of the graphics card and driver, if you can provide info about your graphics card that would be helpful. The command below should provide some info if you don't know what card is in your system.
```

lspci

```

---

### Post by jlh68 on 2008-04-24
I have a PNY nvidia geforce 7300GT 256MB graphics card. It has VGA out, DVI out, and S-Video out.

I read somewhere that nvidia has a Linux control panel, but I do not know how to get it.

And yes you are probably correct that it is a function of the graphics card.

---

### Post by ryanhaigh on 2008-04-24
The control panel can be opened by pressing alt-f2 and entering nvidia-settings. If you want to make the changes permanent by saving the settings to xorg.conf you will need to use gksudo nvidia-settings instead to give the application admin priviliges.

---

### Post by jlh68 on 2008-04-25
Thanks, I will try that when I gget home.

---

### Post by jlh68 on 2008-04-28
I could not get nvidia settings using the [alt]+[F2] keystroke. Maybe some help in what should be entered to get rotation.

I am now reading that the new Screen Resolution utility  rotates a second monitor. I don't know about the first monitor.

Your continued help will be appreciated.

---

### Post by ryanhaigh on 2008-04-28
Have you installed the nvidia driver using restricted driver manager?

If so then what about if you try running nvidia-settings in the terminal?

---

### Post by jlh68 on 2008-04-29
Last night I did install the restricted nvidia driver and I now can get to the nvidia control panel.  With all the settings in it, I still cannot make my primary monitor image to rotate.  I am sure that sooner or later that what to do to get it to work it will surface.  

Other than that, I really like how 8.04LTS works. I have been using the 32-bit Ubuntu although I have my PC set up to dual boot with the 64-bit Ubuntu.  As of yet I have not seen any difference between the two.

---

### Post by ryanhaigh on 2008-04-29
Reading the manual page for the nvidia driver (man nvidia) it seems you have to add the option highlighted below to xorg.conf. 
> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    **Option         "RandRRotation" "on"**
EndSection


This is actually from my own configuration, I added it to test whether it would work and indeed it does. Make this change, logout, press ctrl-alt-backspace to restart x, login again and then you can use the following from the terminal to rotate the display:
```

xrandr -o left
#and to get it back to normal
xrandr -o normal

```

Answering your query has taught me a little about randr/xrandr and why they are useful so thankyou.

---

### Post by mikef_542 on 2008-05-07
Thank you for this post this really helps me out.

I have dual monitors set up on my dell desktop with a nvidia video card in TwinView mode. When I use xrandr to set the orientation both monitors change. Even through I set the option RandRRotation on only the screen I want left orientation.

Do you know if I need to be in the dual desktop mode to have one monitor normal and the other left?

---

### Post by ryanhaigh on 2008-05-07
You should probably provide the output of the command ```
xrandr -q
``` so that we can give more precise instruction.

Assuming you have something like:
> 
$  xrandr -q 
Screen 0: minimum 320 x 200, current 2624 x 1200, maximum 2624 x 2048
VGA connected 1600x1200+1024+0 (normal left inverted right) 367mm x 275mm
   1600x1200      60.0*+
   1920x1440@60   60.0  
   1600x1200@60   60.0  
   640x480@60     60.0  
   640x480        60.0  
LVDS connected 1024x768+0+0 (normal left inverted right) 304mm x 228mm
   1024x768       60.0*+   50.0  
   800x600        60.3  
   640x480        60.0     59.9  
TV disconnected (normal left inverted right)


I believe the command you need to use to set the orientation on the external monitor would be: ```
xrandr --output VGA -o left
```. The name of the output may be different, for me my display is callled default.



EDIT: I just tried this myself but for some reason even using xrandr -o left no longer works for me. I have however found the way to rotate my display, but I had to reduce the resolution ```
xrandr --output default --mode 1024x768 --rotate left
```. It seems rotation is different from orientation, you may need to add a custom mode eg. 1024x1280 then use that mode when rotating.

---

