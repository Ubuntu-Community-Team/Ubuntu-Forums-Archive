---
title: "Screen Resolution issue."
date: 2012-12-26
forum: General Help
---

### Post by morbidyogi on 2012-12-26
I am on Ubuntu 12.10 using a widescreen LCD 17" monitor and motherboard (which is Intel DH67CL) with Intel HD Graphics 2000, no GPU.

Maximum resolution of 1024x768 (4:3) it shows on Ubuntu as well as in xrandr even though the monitor is widescreen. I followed a lot of codes to add new modes nothing seems to work out whereas on Windows my resolution is 1366x768.

My motherboard doesn't have a VGA port, it has a DVI port and I am using DVI to VGA converter to be able to plug VGA on the monitor.

When giving commands I tried writing both 'VGA' and 'DVI'. Still not solved.

"gtf 1366 768 60" and

"xrandr --newmode "1366x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -Hsync +Vsync"

"xrandr --addmode VGA 1366x768_60.00"
"xrandr --addmode DVI 1366x768_60.00"

Says cannot find output.

---

### Post by cwsnyder on 2012-12-26
What is the output of **xrandr** without anything else on the command line? For example, on my desktop, it is:```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1280x1024      59.9* 
```This shows that my output to use for xrandr commands is VGA-1 (beginning of the 2nd line of output), shows the valid screen resolutions set before you ran the xrandr line, the current resolution is shown by the * at the last line, and shows the maximum resolution defined by my present video card settings as 4096x4096.

---

### Post by ranger1021994 on 2012-12-26
> **morbidyogi said:**
> I am on Ubuntu 12.10 using a widescreen LCD 17" monitor and motherboard (which is Intel DH67CL) with Intel HD Graphics 2000, no GPU.

Maximum resolution of 1024x768 (4:3) it shows on Ubuntu as well as in xrandr even though the monitor is widescreen. I followed a lot of codes to add new modes nothing seems to work out whereas on Windows my resolution is 1366x768.

My motherboard doesn't have a VGA port, it has a DVI port and I am using DVI to VGA converter to be able to plug VGA on the monitor.

When giving commands I tried writing both 'VGA' and 'DVI'. Still not solved.

"gtf 1366 768 60" and

"xrandr --newmode "1366x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -Hsync +Vsync"

"xrandr --addmode VGA 1366x768_60.00"
"xrandr --addmode DVI 1366x768_60.00"

Says cannot find output.

I guess there maybe an issue with your graphic card driver.
The drivers specify and enable additional display modes.
Correct me if i am wrong

---

### Post by cwsnyder on 2012-12-26
@ranger1021994: What you said about the graphic card driver is correct . . . if and only if the graphics system reads the EDID of the monitor properly, which I have seen several VGA only displays in which the EDID is not read properly.

If it is read properly, an updated driver may fix the problem.

---

### Post by morbidyogi on 2012-12-26
I tried these codes and it worked for me to get a higher new resolution, making it 16:9, finally.

"gtf 1366 768 60" and

"xrandr --newmode "1366x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -Hsync +Vsync"

"xrandr --addmode VGA**'1'** 1366x768_60.00"

@cwsnyder: I did see the output of xrandr and I noticed I used VGA in that command instead of VGA1. Rookie mistake. Sorry.

Thank ya'll. :)

Though, it still does not detect any display/graphics and shows Unknown.

What do I do about graphics drivers? It is Intel HD 2000. Couldn't find any drivers.

---

### Post by morbidyogi on 2012-12-27
This xrandr setting is limited to a particular session only. I have to command each time I logon.

How do I make this setting permanent? (linux noob here)

---

### Post by fantab on 2012-12-27
There is script [**HERE**]("http://ubuntuforums.org/showpost.php?p=11503588&postcount=4") to enable the resolution permanently. Try if it works.

---

### Post by cwsnyder on 2012-12-28
In my Ubuntu install, I changed the lightdm.conf file to include the **xrandr** lines. (I forgot which tutorial I followed, it has been a while.)  You should also be able to write a shell script with the **xrandr** lines needed, just as you would type them in a terminal.  If you name it **.xinitrc** and place it in your **/home/<username>/** folder and use **chmod +x ~/.xinitrc** to make it executable, it should execute every time you log in.  On my Linux Mint Debian Edition Xfce install, it was renamed by an upgrade to **~/.xprofile**, so if **~/.xinitrc** doesn't work, try **mv ~/.xinitrc ~/.xprofile**, and see if that works for you.

---

