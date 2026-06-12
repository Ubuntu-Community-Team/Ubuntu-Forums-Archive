---
title: "Make resolution changes persistent"
date: 2013-11-20
forum: General Help
---

### Post by Adler on 2013-11-20
>                             The settings are stored in $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml. 

TOZ,

**Thanks for that! **I have been looking for this forever, plus using *cvt *and *xrandr *in Terminal! Now, before I **torch **my system again, I thought I would ask a question.

My screen resolution seems to be able to be greatly improved according to *xrandr *e.g.:

```
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0x11a)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz
  1400x900_60.00 (0x11b)  103.5MHz
        h: width  1400 start 1480 end 1624 total 1848 skew    0 clock   56.0KHz
        v: height  900 start  903 end  913 total  934           clock   60.0Hz
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ 
```

As you can see I am shooting for a screen resolution of either 1600x900, or 1440x900. I could easily slot any of these vales into HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, but I don't want to loose my display. LOL!

If, when I make the change, I re-boot, and I only have a blank screen, how can I recover to change the value back to my present value?

Thanks in advance for your help.

Adler

---

### Post by Toz on 2013-11-20
What version of Xfce (or Xubuntu) are you using?

Your laptop screen is capable of a maximum resolution of 1366x768. 
Your external monitor is capable of a maximum resolution of 1600x900. 

How exactly are you trying to set up your monitors? If its to create one big screen, does:
```
xrandr --output DP1 --auto --right-of LVDS1
```
...work?

---

### Post by Adler on 2013-11-20
> What version of Xfce (or Xubuntu) are you using?

Toz,

I am running XFCE 4.8, and 12.04 LTS. I just ran *xfce4-about* in Terminal.

> Your laptop screen is capable of a maximum resolution of 1366x768. 

If that is so you have just put me in the know! I am under the mistaken impression that I could go higher e.g. at least to 1920x1080 < 32767x32767. I've just run *xrandr *again, after a re-boot:

[B]adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ 

[/B]Basically, I am just tweaking my H-P Ultrabookdisplay, and not multiple displays.> xrandr --output DP1 --auto --right-of LVDS1That didn't do anything.

Toz, thanks for the reply!

Adler

---

### Post by Toz on 2013-11-20
> **Adler said:**
> Toz,

I am running XFCE 4.8, and 12.04 LTS. I just ran *xfce4-about* in Terminal.



If that is so you have just put me in the know! I am under the mistaken impression that I could go higher e.g. at least to 1920x1080 < 32767x32767. I've just run *xrandr *again, after a re-boot:

[B]adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ 

[/B]Basically, I am just tweaking my H-P Ultrabookdisplay, and not multiple displays.That didn't do anything.

Toz, thanks for the reply!

Adler

According to the results of xrandr after reboot, you don't have anything showing up for DP1 (external monitor) but only for LVDS1 (laptop screen). And yes, its maximum resolution is 1366x768. So the command I noted won't work on a laptop-only display, you need to have an external monitor attached (which I thought you did based on the results of your previous xrandr command results).

---

### Post by Bucky Ball on 2013-11-20
***Post(s) move to own thread.***

---

### Post by Adler on 2013-11-20
> And yes, its maximum resolution is 1366x768.

Toz,

Thanks again for your reply. I guess I was mis-lead by the results of *xrandr *thinking I could exceed my present resolution.

Adler

---

