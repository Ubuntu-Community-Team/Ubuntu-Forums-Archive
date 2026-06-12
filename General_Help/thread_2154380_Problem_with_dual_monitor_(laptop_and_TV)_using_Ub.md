---
title: "Problem with dual monitor (laptop and TV) using Ubuntu 12.10"
date: 2013-06-14
forum: General Help
---

### Post by brunces on 2013-06-14
Hey, guys. What's up? :)

I have this problem and I can not figure out how to solve it. Yesterday, I bought this PC-TV converter (Comtac)...

[http://www.comtac.com.br/?url=produto&id=224](http://www.comtac.com.br/?url=produto&id=224)

By the way, I'm from Brazil and the converter "is" compatible with Linux.

I have a Samsung laptop...

[http://www.samsung.com/br/support/model/NP-RV411-AD6BR-techspecs](http://www.samsung.com/br/support/model/NP-RV411-AD6BR-techspecs)

(Summarizing, it has an i5 processor with 4 GB of RAM and an Intel GMA HD graphics card.)

I use Ubuntu 12.10, with the new Intel drivers installed, based on their recommendation...

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1)

My intention is to work with two screens at the same time: the laptop screen (of course) and a 29" TV (old one)...

[http://images04.olx.com.br/ui/20/79/71/1337565100_345767871_2-Fotos-de--TV-29-polegadas-SEMP-TOSHIBA.jpg](http://images04.olx.com.br/ui/20/79/71/1337565100_345767871_2-Fotos-de--TV-29-polegadas-SEMP-TOSHIBA.jpg)

This is the output I get for the "xrandr -q" command:

```
Screen 0: minimum 320 x 200, current 2390 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.2*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

It shows I'm using 1024x768 for the TV resolution, but I've also tested 800x600 and 640x480, with no success, using these commands:

```
xrandr --output VGA1 --mode 800x600 --rate 60
xrandr --output VGA1 --mode 640x480 --rate 60
```

I've also installed "arandr", but it didn't help.

PROBLEM:

Everything is properly connected:
- a VGA cable from the laptop to the converter;
- an RCA cable from the converter to the TV.

When I turn on the converter (USB plug), the TV shows my extended screen, as expected, however the image disappears and the TV screen gets blank after 2 seconds. Then, after 2 more seconds, the TV shows the extended screen again. Then, 2 seconds later, it disappears and the screen gets blank again. And it goes on and on with this "appearing/disappearing image" loop.

Having the "System Settings - Displays" window open, it is possible to notice that, when the TV screen gets blank, the second monitor is "disabled", as if I had disconnected the VGA cable from the laptop. Then, when the image comes back on the TV screen, the second monitor is "enabled" again, as if I had reconnected the VGA cable.

I've tested the converter on a PC with Windows 7, and it worked flawlessly, so it seems to be a problem with Ubuntu, not with the converter itself.

Well, according to the scenario mentioned and to your experience, what do you think it can be? Is there any settings missing in my system? I really need to get this to work. If you can help me, I will really appreciate it.

Thanks in advance, guys.

brunces

---

### Post by gordintoronto on 2013-06-14
What old TV technology was (?) used in Brazil? In North America, analogue TVs were equivalent to "480I". You might try "640X480 rate 30".

Did you test the converter on the same PC, running Windows?

---

### Post by brunces on 2013-06-14
[COLOR=#000000]gordintoronto, thanks for your answer.
[/COLOR]
According to the manual of the converter, I'm afraid I can't use rate 30 with resolution 640x480. Please, take a look at their recommendation on page 7...

[http://www.comtac.com.br/download/manual/9158.pdf](http://www.comtac.com.br/download/manual/9158.pdf)

Anyway, as far as I know, the specification for this TV of mine is 640x480@56-60Hz (480p, if I'm not wrong).

Yes, as I said before, I've tested the converter on a PC with Windows 7, and it worked flawlessly, so it seems to be a problem with Ubuntu, not with the converter itself.

Still looking for a solution. :/

Thanks again for your time.

brunces

---

### Post by gordintoronto on 2013-06-15
Would it be possible to boot the Windows 7 computer from an Ubuntu LiveCD or LiveUSB, and see if that works?

Converters are a frequent source of grief, and you can't be certain that the laptop hardware contributes to the problem.

BTW, analogue TVs were interlaced, so 480I not 480P. Did you try 30?

---

### Post by brunces on 2013-06-15
gordintoronto, take a look at this video I just made, please:

[http://www.youtube.com/watch?v=raIIVcFx-OI](http://www.youtube.com/watch?v=raIIVcFx-OI)

As I described on my first post, and you can see for yourself now, the image keeps on appearing and disappearing on the TV, over and over, until I unplug the converter (USB). Also, you can notice that when the image disappears on TV, the second monitor gets "disconnected" on "Displays" window, as if I had unplugged the VGA cable. Weird!

Just for the record, before filming, I just plugged in the converter (USB); but while filming, I did not touch my laptop computer.

I'm using a smaller TV (14" Philips) now because my wife is watching TV right now (the 29" one), but the behavior is the same on both.

I tried rate 30, as you suggested. Problem remains.

By the way, you're right, it is 480I, indeed.

---

