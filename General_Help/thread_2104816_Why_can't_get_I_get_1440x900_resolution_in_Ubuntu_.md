---
title: "Why can't get I get 1440x900 resolution in Ubuntu anymore?"
date: 2013-01-14
forum: General Help
---

### Post by DifferentTrains on 2013-01-14
I've been using Ubuntu since 6.06 and it's a great OS. I've also used Debian and Slackware and some other Debian-based distros. So I know a bit about Linux but this has got me stumped...!

A few weeks ago, my Ubuntu 12.04 stopped letting me use the 1440x900 resolution I'd had for over a year. First it limited me to 1024x768, now I am limited to 1360x768. 

I have googled and tried a few things but nothing seems to be able to get me my 1440x900 resolution back. I've even re-installed several times and replaced the monitor cable and tried another monitor and another video card. Installing or not installing proprietary drivers after re-installation also seems to make no difference. 

I used to be able to hack things using the "dpkg-reconfigure xserver-xorg" command or by editing xorg.conf . These now seem to be obsolete, which is a shame.

During my google searches, whilst I've come across many people with similar problems, none of the solutions listed have worked for me so far. I have noticed a few suggesting it might be a kernel upgrade gone wrong?

My graphics card is a:
```
02:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)

```and xrandr says the following:
```

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 406mm x 229mm
   1360x768       60.0*+
   1280x768       59.9  
   1024x768       75.1     75.0     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1  

```

---

### Post by DifferentTrains on 2013-01-19
bump!

Surely there must be someone out there who has an answer to this irritating problem? Google searches show I am far from the only one having it! (yet none of those solutions work for me!)

Forgot to mention in the above post that I also obviously tried all the drivers available. Many of them actually make my graphics worse by causing screen flickers on top of not being able to get the correct resolution. 

I found an old live CD of 7.10 and booted that up and had the same problem, so it can't be the kernel.

I just don't understand why Ubuntu has been working fine for years and been able to set the correct resolution and now suddenly not been able to anymore.

---

### Post by BlinkinCat on 2013-01-19
No help but -

I just wanted to remind you that 24 hour bumps are considered reasonable in the forums.

I hope you get your problem resolved - :)

---

### Post by bab1 on 2013-01-19
> **DifferentTrains said:**
> ...DVI-I-1 disconnected (normal left inverted right x axis y axis)

Is the monitor digital (does it have a DVI connector).  The video card has a digital output.  A digital capable monitor ID's itself to the OS (Xorg) and the rez is automagically set.  I believe 1440x900 is a digital setting only.

---

### Post by DifferentTrains on 2013-01-19
> **bab1 said:**
> Is the monitor digital (does it have a DVI connector).  The video card has a digital output.  A digital capable monitor ID's itself to the OS (Xorg) and the rez is automagically set.  I believe 1440x900 is a digital setting only.

My video card has both digital and VGA outputs, but my monitor only has a VGA plug, so I use the VGA. I had it working in the past using the same setup, so I don't really understand how it can be digital only?
Could I fool ubuntu by using a digital to VGA converter at the monitor end? Worth a try?

---

### Post by DifferentTrains on 2013-01-20
24 hour bump time! ;)
Thanks for the heads up on that rule!

---

### Post by Mark Phelps on 2013-01-20
Sorry you got no more replies, but you might have done better if you had posted this in the video section, instead of General.

Anyway ... the link below is to a page listing the xrandr parms. Since your output has the mode you want within the max limits, I would try issuing the command manually using different settings -- as some of the example show:

[https://wiki.archlinux.org/index.php/Xrandr]("https://wiki.archlinux.org/index.php/Xrandr")

---

### Post by bab1 on 2013-01-20
> **DifferentTrains said:**
> ...
Could I fool ubuntu by using a digital to VGA converter at the monitor end? Worth a try?

Maybe...

I would first try and set the proper mode (or close to it) first.  This site might also help you:
[_[COLOR="Blue"]http://xtiming.sourceforge.net/cgi-bin/xtiming.pl[/COLOR]_]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

---

### Post by DifferentTrains on 2013-01-23
Still going round in circles...

```

dusepo@dusepo-desktop:~$ xrandr --newmode "1440x900_60" 108.84 1440 1472 1880 1912 900 918 927 946
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25
dusepo@dusepo-desktop:~$ xrandr --addmode VGA-1 "1280x900_60"
xrandr: cannot find mode "1280x900_60"

```*sigh*

---

### Post by Bobhuber on 2013-01-23
The newer nvidia drivers are causing the problem (at least in my case) going back to the 295.71 drivers along with a kernel that supports that driver fixed my problem.

---

### Post by zainka on 2013-01-24
Hmm... You said you tried an older ubuntu (7.10) and problem was the same. If running live CD I guess u are using the default gfx driver that comes with the cd, but if installing instead  I guess it updates with latest from the net for a given ubuntu release. This could have changed back and forth many times between 7.10 and 12.04. Why not try last 11.xx version? 

It is problems and changes like these that actually holds back Linux to gain more momentum in the marked. Most people get tierds of these tweaks all the time. I am not.....

However, My actual reason for posting was this blog that deals with missing screen resolution options by using xrandr at command line. Read on at:

[http://wienker.org/blog/?p=32](http://wienker.org/blog/?p=32)

enjoy!

---

