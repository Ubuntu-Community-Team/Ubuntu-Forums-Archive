---
title: "1440x900 Not Working"
date: 2014-08-11
forum: General Help
---

### Post by Kale_Freemon on 2014-08-11
Hello all! I'm hoping that someone will be able to help me out with this issue.

I am currently running an older machine with an integrated Intel HD Graphics GPU from 2010. I have it plugged into my TV via HDMI. 

In Windows I am able to use a resolution of 1440x900 at 60Hz and it works great for me. But, under Xubuntu 14.04, when I try to set the same resolution, it only works at 59Hz and it doesn't display properly at all.

Here's a couple of pictures I took to demonstrate.

Ubuntu:

[http://i58.tinypic.com/14ec2rn.jpg](http://i58.tinypic.com/14ec2rn.jpg)


Windows:

[http://i58.tinypic.com/inzyba.jpg](http://i58.tinypic.com/inzyba.jpg)



Anyway to possibly fix this issue?

Thanks in advance!

---

### Post by ajgreeny on 2014-08-11
What is the output of **xrandr** in terminal?

Does it show the wanted 1440x900 in the listed resolutions?

---

### Post by Kale_Freemon on 2014-08-11
I can tell you that, by running xrandr in the terminal, 1440x900 is in the listed resolutions. However, it only lists it as 59Hz in xrandr. I can post the full output in a little bit. I'm currently in my Windows partition, waiting on a process to complete.

---

### Post by ajgreeny on 2014-08-11
Don't worry too much about the 59Hz; that should be near enough for display purposes.  This is what I get
```
~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0* 
   1400x1050      59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     66.0     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

However, I wonder if this is something to do with the TV as opposed to a normal monitor being used for the output.

---

### Post by Kale_Freemon on 2014-08-11
Here's me. The LVDS1 is my laptop's display. But I don't use that. HDMI1 is the one in use.

```
$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080i     60.1 +   60.0  
   1920x1080      60.0     59.9  
   1280x1024      60.0* 
   1440x900       59.9  
   1360x768       60.0  
   1280x768       59.9  
   1280x720       60.0     59.9  
   1024x768       75.1     70.1     60.0  
   1440x480i      60.1     60.1     60.1  
   800x600        72.2     75.0     60.3     56.2  
   720x480        60.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


```

I'm inclinded to think similarly to you when it comes to the fact that I am using a TV as opposed to a regular monitor. However, the fact that it works in Windows, and that I was able to make it work back before 12.10, makes me wonder if there's another issue somewhere.

---

### Post by Rev2010 on 2014-08-11
I've had similar issues with hdmi, though not necessarily ubuntu. To fix I had to go into my TV settings and change the scan option. For example, my Samsung TV has a setting called "just scan". Sometimes that needs to be on, others I have to switch it to the other option, which I can't recall at the moment since I'm not in front of my TV. Come to think it, I believe I've experienced this with vga as well. Try your TV settings, you'll probably be able to resolve it through there. As mentioned, there's no problem with 59hz. Actually, true refresh rate is 59.97. 


Rev.

---

### Post by nerdtron on 2014-08-11
I remember before on Xubuntu 12.10 I was able to get 1440x900 native resolution by the following command.

```
xrandr --size 1440x900
```

Try it with sudo if it doesn't work.

Or are you using dual monitors or external display cable? Try installing **arandr **from the software center. It's a little GUI program for managing screen resolution.

---

### Post by Kale_Freemon on 2014-08-11
> **Rev2010 said:**
> I've had similar issues with hdmi, though not  necessarily ubuntu. To fix I had to go into my TV settings and change  the scan option. For example, my Samsung TV has a setting called "just  scan". Sometimes that needs to be on, others I have to switch it to the  other option, which I can't recall at the moment since I'm not in front  of my TV. Come to think it, I believe I've experienced this with vga as  well. Try your TV settings, you'll probably be able to resolve it  through there. As mentioned, there's no problem with 59hz. Actually,  true refresh rate is 59.97. 


Rev.

Unfortunately, it does not appear that my TV has that kind of  option. It's a cheapo one that I bought from Walmart a couple years  back. I've tried just about every available option in the menu, and to  no avail.




> **nerdtron said:**
> I remember before on Xubuntu 12.10 I was able to get 1440x900 native resolution by the following command.

```
xrandr --size 1440x900
```

Try it with sudo if it doesn't work.

Or are you using dual monitors or external display cable? Try installing **arandr **from the software center. It's a little GUI program for managing screen resolution.

The command doesn't work. All it does is sets in in the resolution, but it still looks just like it did in the image in my original post. I've got it plugged in via HDMI. I am not using a dual monitor set up. I'll give that program a try.

EDIT: Ya. arandr is a no go too. Darn.

EDIT2: Well, I much appreciate the attempt. I'm thinking there is no solution to this problem. As such, I have decided to live with a [COLOR=#000000][FONT=Ubuntu Mono]1360x768 resolution for the time being, until this problem can be resolved, or I can get new hardware. [/FONT][/COLOR]

---

### Post by ajgreeny on 2014-08-12
Are you certain that the native resolution of the TV really is 1440x900?

---

### Post by trag on 2014-08-12
Your TV can only receive a fixed number of HDMI resolutions,and your PC can only send a fixed number of HDMI resolutions. Simply put your pc is pitching an HDMI signal that your TV is not designed to receive thus your getting overscan.you will need an hdmi/vga adapter, with this in place sound will pass to your tv via hdmi while your video signal will be converted to vga. Set your tv to recieve vga signals and all will be well.
good luck
Trag

---

