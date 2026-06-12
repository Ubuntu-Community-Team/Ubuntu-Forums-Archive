---
title: "Screen freezes. Ubuntu 16.04"
date: 2017-02-21
forum: General Help
---

### Post by lferrez on 2017-02-21
Hello all,

As o f lately one of our computers' screen constantly freezes. I have rebuilt the system at least twice now, updated video card drivers. But I get feedback from user that screen  freezes  (only mouse moves) every several hours.

It seems like the computer is fine when I do basic tasks like web browsing and running commands from terminal, however I have a user who experiences computer freeze on a regular basis when running multiple applications, doing Bioinformatics analysis using R, Matlab and miscellaneous open source software.

Below is the output I get when I run $ inxi -ACDMNSG



 
 [COLOR=#0000ff]**System:**[/COLOR] [COLOR=#0000ff]**Kernel:**[/COLOR][COLOR=#0000ff] [/COLOR]4.4.0-62-generic x86_64 (64 bit)

            	     	[COLOR=#0000ff]**Desktop: **[/COLOR]Unity 7.4.0 [COLOR=#0000ff]**Distro:**[/COLOR][COLOR=#0000ff] [/COLOR]Ubuntu 16.04 xenial

 [COLOR=#0000ff]**Machine:  **[/COLOR] 	[COLOR=#0000ff]**Mobo:**[/COLOR]ASUSTeK [COLOR=#0000ff]**model:**[/COLOR]RAMPAGE IV BLACK EDITION[COLOR=#0000ff]**v:**[/COLOR][COLOR=#0000ff] [/COLOR]Rev 1.xx
                    	[COLOR=#0000ff]**Bios:**[/COLOR]American Megatrends [COLOR=#0000ff]**v:**[/COLOR] 0701 [COLOR=#0000ff]**date:**[/COLOR] 06/04/2014
 [COLOR=#0000ff]**CPU:  **[/COLOR][COLOR=#0000ff]  [/COLOR]   	[COLOR=#0000ff]**Hexa core**[/COLOR] Intel Core i7-4960X (-HT-MCP-) [COLOR=#0000ff]**cache:**[/COLOR]15360 KB  
             	[COLOR=#0000ff]**clock speeds:**[/COLOR][COLOR=#0000ff]**max:**[/COLOR]4000 MHz [COLOR=#0000ff]**1:**[/COLOR]1997 MHz [COLOR=#0000ff]**2:**[/COLOR] 1714 MHz [COLOR=#0000ff]**3: **[/COLOR]1522 MHz
            		[COLOR=#0000ff]**4:**[/COLOR]2901 MHz[COLOR=#0000ff]**5:**[/COLOR] 1255 MHz [COLOR=#0000ff]**6: **[/COLOR]1241 MHz [COLOR=#0000ff]**7:**[/COLOR]1336 MHz [COLOR=#0000ff]**8: **[/COLOR]1357 MHz
           		[COLOR=#0000ff]**9:**[/COLOR]1550 MHz [COLOR=#0000ff]**10: **[/COLOR]1680 MHz [COLOR=#0000ff]**11: **[/COLOR]2408 MHz [COLOR=#0000ff]**12:**[/COLOR][COLOR=#0000ff] [/COLOR]1443 MHz
 [COLOR=#0000ff]**Graphics: **[/COLOR]	[COLOR=#0000ff]**Card:**[/COLOR]NVIDIA GK106 [GeForce GTX 660]
            		[COLOR=#0000ff]**Display Server:**[/COLOR][COLOR=#0000ff] [/COLOR]X.Org 1.18.4 [COLOR=#0000ff]**drivers: **[/COLOR]nvidia (unloaded: fbdev,vesa)
            		[COLOR=#0000ff]**Resolution:**[/COLOR] 1280x1024@60.02hz
            		[COLOR=#0000ff]**GLX Renderer:**[/COLOR] GeForce GTX 660/PCIe/SSE2
            		[COLOR=#0000ff]**GLX Version:**[/COLOR] 4.5.0 NVIDIA 367.57
 [COLOR=#0000ff]**Audio:**[/COLOR]    	[COLOR=#0000ff]**Card-1**[/COLOR]NVIDIA GK106 HDMI Audio Controller [COLOR=#0000ff]**driver:**[/COLOR][COLOR=#0000ff] [/COLOR]snd_hda_intel
            		[COLOR=#0000ff]**Card-2**[/COLOR][COLOR=#0000ff] [/COLOR]Intel C600/X79 series High Definition Audio Controller
           		[COLOR=#0000ff]**driver: **[/COLOR]snd_hda_intel
            		[COLOR=#0000ff]**Sound: **[/COLOR]Advanced Linux Sound Architecture [COLOR=#0000ff]**v:**[/COLOR]k4.4.0-62-generic
 [COLOR=#0000ff]**Network:  **[/COLOR][COLOR=#0000ff] [/COLOR]	[COLOR=#0000ff]**Card: **[/COLOR]Intel 82579V Gigabit Network Connection [COLOR=#0000ff]**driver:**[/COLOR] e1000e
 [COLOR=#0000ff]**Drives:**[/COLOR][COLOR=#0000ff] [/COLOR]   	[COLOR=#0000ff]**HDD Total Size:**[/COLOR] 1480.3GB (56.5% used)
            		[COLOR=#0000ff]**ID-1:**[/COLOR][COLOR=#0000ff] [/COLOR]/dev/sda [COLOR=#0000ff]**model:**[/COLOR] SSD2SC480G5LC763 [COLOR=#0000ff]**size:**[/COLOR]480.1GB
            		[COLOR=#0000ff]**ID-2:**[/COLOR][COLOR=#0000ff] [/COLOR]/dev/sdb [COLOR=#0000ff]**model:**[/COLOR][COLOR=#0000ff] [/COLOR]ST1000DM003 [COLOR=#0000ff]**size:**[/COLOR]1000.2GB

Any idea of what may be causing this or what may be a fix to this problem?

Thank you.

---

### Post by dragonfly41 on 2017-02-21
From my own recent experience on a much older laptop ...

Provided that cursor continues to move (as you confirm) ..

Select Ctrl+Alt+F1 to switch to TTY
then when that appears switch back using Ctrl+Alt+F7

You might see a browser popup window with message "unresponsive script"
which you would otherwise not see .. suggesting a tab is stuck (perhaps running a large script or video).

There are more intensive tests you might run for troubleshooting freezes .. which are difficult to pin down 

install GKrellM.
This is more comprehensive tool than System Monitor.

I can point you to some articles I found recently explaining how to use
 the desktop version and server version 
(where you could remotely inspect the user's system via SSH)

[https://totallynoob.com/server-monitoring-remote-monitor-a-server-with-gkrellm-via-ssh-tunnel/](https://totallynoob.com/server-monitoring-remote-monitor-a-server-with-gkrellm-via-ssh-tunnel/)

[http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-gkrellmd-to-monitor-linux-boxes-automatically/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-gkrellmd-to-monitor-linux-boxes-automatically/)

[http://nst.sourceforge.net/nst/docs/faq/ch03s03.html](http://nst.sourceforge.net/nst/docs/faq/ch03s03.html)

---

### Post by efflandt on 2017-02-21
When I had a similar issue (basically stopped responding to key presses  or mouse buttons, but mouse cursor still moved) it was a failing  graphics card (cheap GT 430 from Galaxy just after 1 year warranty  expired). But it would happen randomly primarily in the desktop,  sometimes right after booting or sometimes after having no problems  playing minecraft for hours. Prior to that Win7 would report something  like "Graphics driver stopped responding, recovered" regardless of trying various  Nvidia drivers. Sometime later I got boot errors in Ubuntu that the  graphics hardware was not responding or sometimes scrambled graphics.  Since then same PC has not had that problem with EVGA GTX 550 Ti (3 yr  warranty) that I used for several years (Ubuntu 12.04), MSI GTX 750 Ti  (Ubuntu 14.04), or current GTX 1060 (Ubuntu 16.10 w/nvidia-375 or  nvidia-378 drivers from ppa).

So I cannot tell you if it is a graphics card issue. But I did have a similar problem with a failing graphics card in the past. Nvidia may make the chips, but others make the cards.

---

### Post by bennylp on 2017-12-18
Fast forward to Dec 2017, and same issue. Sometimes the desktop freezes, usually able to switch to tty1 and back few times, until unable to do so and had  to hard boot the machine. Usually the problem would reappear, until it doesn't. When it doesn't, the system would run for few days without a problem. All under light use (mostly browsing). Has anyone figure out a workaround? 

- Ubuntu 16.04
- Linux 4.10.0-42-generic
- Intel i7-6700 16GB
- Zotac Mini GTX 1080
- nvidia-387 driver

---

