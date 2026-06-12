---
title: "HOWTO: Fix Gutsy External Display Issues"
date: 2007-10-26
forum: General Help
---

### Post by Vaan on 2007-10-26
This may or may not fix your particular issue, but I hoped this thread could be used to discuss various display issues that all (or most) seem to stem from one particular new "problem" with Gutsy.

In my case, once I upgraded to Gutsy my internal and external display were both activated and running at the same time (unlike Feisty where only my external monitor would be the active display) and this caused some weird issues like windows resizing for the wrong resolution and such giving it a superimposed-like look on my external display.

The main culprit is this new dynamic screen configuration application Gutsy uses called **Xrandr**.

Open up a terminal and type in *xrandr* and you should be presented with some display information. Type in *xrandr -h* and you get some additional information on available options.

What I did was shutdown my internal (notebook) display and this fixed the problem I was having with the toolbars and such resizing for the wrong resolution on the external display.

I did it via this command:

*xrandr --output LVDS -off*

That seemed to have solved my issue at least temporarily. I'm going to tinker around with it some more and see what else I come up with. I'm hoping this will help out some users who have similar issues with their display.

---

### Post by mlissner on 2007-10-26
I tried this...it didn't help with my problem, which is that when I maximize windows, they only go as big as my laptop screen even though that's off and I have an external display running.

For the record though, the command above is:
```
xrandr --output LVDS --off
```

---

### Post by Bakey on 2007-10-26
Hey mlissner, did you try disabling desktop effects as mentioned here:
[http://ubuntuforums.org/showthread.php?t=582551](http://ubuntuforums.org/showthread.php?t=582551) ?

Also, if you don't mind, add on to the bug report below about what hardware you're using that you're seeing this problem with.

[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/154453](https://bugs.launchpad.net/ubuntu/+s...iz/+bug/154453)

---

### Post by TubaTodd on 2007-10-26
Ditto. I tried the command and it didn't work for me either. The LVDS screen was still listed as connected.

---

### Post by mlissner on 2007-10-26
> **Bakey said:**
> Hey mlissner, did you try disabling desktop effects as mentioned here:
[http://ubuntuforums.org/showthread.php?t=582551](http://ubuntuforums.org/showthread.php?t=582551) ?

Also, if you don't mind, add on to the bug report below about what hardware you're using that you're seeing this problem with.

[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/154453](https://bugs.launchpad.net/ubuntu/+s...iz/+bug/154453)

I haven't tried disabling desktop effects, because, frankly, I'm scared that if I do I will have to reconfigure them all over again, which I've done twice now...

Frustrating.

---

### Post by Vaan on 2007-10-26
Okay mlissner, run the xrandr command and post the results here. 

Very frustrating, now I'm trying to configure compiz to work properly and it seems to be randomly freezing at times.

---

### Post by mlissner on 2007-10-26
Won't say no to an offer like that. ```
xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1792 x 1344
VGA connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1792x1344@60   60.0  
   1600x1200@65   65.0  
   1600x1200@60   60.0  
   1400x1050@75   75.0  
   1400x1050@60   60.0  
   1280x1024@75   75.0  
   1280x1024@60   60.0  
   1280x960@75    75.0  
   1280x960@60    60.0  
   1152x864@75    75.0  
   1152x864       75.0  
   1024x768@75    75.1  
   1024x768       75.1     70.1     60.0  
   1024x768@70    70.1  
   1024x768@60    60.0  
   832x624@75     74.6  
   832x624        74.6  
   800x600@72     72.2  
   800x600        72.2     75.0     60.3     56.2  
   800x600@75     75.0  
   800x600@60     60.3  
   800x600@56     56.2  
   640x480@72     72.8  
   640x480@75     75.0  
   640x480        75.0     60.0  
   640x480@60     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right)
   1280x800       60.0 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

```

---

### Post by Vaan on 2007-10-26
Ah, but your internal screen does shutdown when you run the command? I'm wondering why you're still getting window resolution problems.

What's your external display resolution?

---

### Post by mlissner on 2007-10-26
Well, the internal screen was actually off before I started because the laptop lid was closed, and it therefore turned off.

That aside, my external resolution is 1280x1024, which isn't the end of the world because my internal resolution is 1280x800 (I think, it's widescreen laptop).

---

### Post by Vaan on 2007-10-26
Still quite annoying. You would thing all of this would've been tested and fixed before release. I'm hoping some others could shed some light on these issues.

I'm trying to figure out where the xrandr config (if there is one) is stored. Each time I reboot I have the same issue and I have to reissue the command. It also affects my logon screen which is a nuisance.

I was contemplating just removing th xrandr package, but apparently it removes about 150MB worth of packages which doesn't look too bright an option.

---

### Post by shonisan on 2008-01-14
I'd love to be having some of these issues.

I am a clean install of Gutsy on a Thinkpad R60 (ATI x1300) and, since I live in the land of cheap monitors (China), I took the leap and bought a generic 19" wide screen (1440x900)  to use as an external.

When I power up, I just boot to black.

I could see it cycling through various resolutions attempting to get it to work.

So I unplugged it and have crawled the forums looking for solutions.

I have tried manually editing xorg.conf and setting the monitor in the System > Administration > Screen and Graphics ... all to no avail.

I have seen the boot splash appear on my wide screen external. I arrive at the login on the internal and sign in. The screen clears ... it 'spins its wheels' for a while and ... goes back to the login screen where I hit cntl-alt-F1 so I can recover xorg.conf and reboot.

I don't want to go off on a rant here but ... I have gone from a University Professor with a passion for making videos to a geek on a very extreme learning curve.

I had intended to divorce myself from the hybrid of a leech crossed with an ex-wife, Mr. Gates, but since I use presentations in the classroom, I find myself restricted to my Windows laptop.

What is the point of a presentation manager like the one in Open Office if you can't easily go from classroom to classroom plugging into various and sundry external devices to actually DO a presentation?

I didn't expect my computer to become my new vocation.

I had a wonderful opportunity to evangelize about the 'wonders of Linux' in my civil engineering classes but was forced to bring up the YouTube comparison of Vista and Beryl on Windows XP reducing me to all the passion and sincerity of Jerry Fallwell giving a lecture on celibacy.
[/rant] ](*,)

Well, I thought you all needed a little comic relief here so remember, I'm still 100% behind Ubuntu and the impressive things it does outside of this one critical issue for me.

:popcorn:

---

### Post by shonisan on 2008-01-14
PS. ATI Doesn't support xrandr

---

### Post by dmonkey on 2008-01-22
Hi,

If you're interested, I wrote a script to automate this process. I also have a laptop running Ubuntu. When I'm at work, I use an external display, so I simply tell Ubuntu if it detects an external display it should turn off my laptop screen. Create a new file called 'fixdisplay' and open it in your favourite text editor. Put the following in the file

```

#!/bin/bash

if xrandr -q | grep -q "TMDS-1 connected"
then
  xrandr --output LVDS --off
fi

exit 0

```

Note: If you have a VGA screen connected, you will need to replace TMDS-1 with VGA.

Now you can test the script by running it in a terminal. Now go to System > Preferences > Sessions and add the script to the list of startup programs. Note that this will not fix the login screen, as these scripts are only executed after login, but for me this isn't a big deal.

Hope you find this useful.

---

