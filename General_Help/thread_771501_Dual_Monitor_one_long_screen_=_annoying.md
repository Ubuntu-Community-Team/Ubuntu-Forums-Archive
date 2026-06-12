---
title: "Dual Monitor: one long screen = annoying"
date: 2008-04-27
forum: General Help
---

### Post by Banter on 2008-04-27
In Hardy, the only option for dual monitors seems to be one painfully long desktop spanning across two monitors with the Applications menu on one end and the clock on the other.

For me, working with dual monitors is the biggest road block in my move from xp to Ubuntu. In xp, it was possible for my laptop screen to display my Windows desktop and my second monitor to display the background of my desktop and nothing else (e.g. no start menu). This was fantastic because I could drag open windows over to my external monitor and have a normal looking desktop on my laptop screen. It was perfect.

Is there a way to achieve in Hardy the dual monitor panacea I found in XP?

Graphics Card: nvidia (Quadro NVS)

---

### Post by ryanhaigh on 2008-04-28
Use nvidia-settings (press alt-f2 and enter nvidia-settings) to setup you X configuration, use twinview rather than xinerama. If you want to make the changes permananent use gksudo nvidia-settings instead and save the configuration to xorg.conf (there is a button to do this).

---

### Post by Ralphie on 2008-04-28
also, make sure you have compiz running, ive found it does a much better job of managing windows on a dual head setup

---

### Post by posterberg on 2008-04-28
Running dual head on my Latitude D430 works a lot worse than it did in Gutsy.

I can't get the built in monitor to go dark, it has "only" 1280x800 in resolution compared to my external screen that has 1600x1200.

The internal screen does always show some part of what the external does. 
It looks like a complete mess. The internal screen has the taskbar aligned slighthly below the center of the screen, but it is nicely aligned at the bottom on the external screen.

I cant get it to use side to side (extended mode) or completely turn it off if I'd prefer that.

Doesn't matter if I am running with or without desktop effects.

---

### Post by ryanhaigh on 2008-04-28
Using nvidia-settings (assuming your laptop has a nvidia card as the OP does) you an disable the monitor by setting it off.

---

### Post by posterberg on 2008-04-28
It doesn't have the same card; Intel 945GM card...

I just thought that my problem also would it did fit under the current thread's topic...

---

### Post by ryanhaigh on 2008-04-28
I have no experience with an intel card and dual monitor setup, you might find information you need in the manual page for the intel driver. Enter man intel in the terminal or search help and support for man intel. It seems you can specify the output to use using randr. 

I really wish there was documentation for randr and xrandr on the ubuntu wiki. I would really like to know more about these as they appear to be very important considering the minimalistic nature of the xorg.conf files used in hardy.

---

### Post by posterberg on 2008-04-28
Thank you! I could use xrandr to blank the laptop's internal monitor.

---

### Post by ryanhaigh on 2008-04-28
For my own reference and anyone else who needs it:
How to use xrandr: [http://www.phoronix.com/scan.php?page=article&item=927](http://www.phoronix.com/scan.php?page=article&item=927)

---

### Post by Banter on 2008-04-29
Ok, I figured out what needs to be done to enable "true" dual screens (independent screens) with nvidia.

[back up your xorg config file!]

First, gksudo nvidia-settings in the terminal.
Second, press the detect button to detect your second monitor then press the config button and select the Separate X screen option.
Third, push the 'save to config file' button.
Fourth, press ctrl + alt + backspace to restart X. (your monitor will shut off momentarily)
Finally, you end up with two independent screens. 

The downside is that compiz is super slow when I do this (but just on my laptop screen, not the external monitor), so you may want to disable it. Also you won't be able to drag windows from one monitor to the next (I don't think).

The upside is that you won't end up with one really long desktop spanning two screens at different resolutions . . . and every time you open a new window it appears in the middle of the two screens . . . and when you maximize it fills both screens up . . . alright I'm done.


Any comments? Please let me know what you think!

---

### Post by ryanhaigh on 2008-04-29
I have seen this issue before with people using twinview having the panels/maximized windows spanning both screens. It is my understanding that in order to prevent this you need to have metamodes in your xorg.conf file. I have attatched my xorg.conf for reference although I should point out that I didn't edit anything but the mouse settings manually, the graphics was all configured through nvidia-settings.

I have also found that compiz handles twinview better than metacity does and most apps will popup on the active display (where the mouse was last clicked) with only a few poping up in the center.

EDIT: perhaps using absolute positioning for the second display in nvidia-settings rather than auto is what writes the metamode information to the file.

---

### Post by svk on 2008-05-26
Thank you very much, ryanhaigh.  I had the same issue and found this thread on google.  After manually setting the position for the second display (instead of auto) in nvidia-settings, saving the config to xorg.conf, and restarting X, I finally got dual display to work almost as well as it does in Windows.

I've been using separate X screens until now, but it was incredibly annoying -- mostly because of firefox, because you can only have one instance running on the entire system.  Being able to drag windows from one display to the other is a relief, too.

---

### Post by khughitt on 2008-06-13
If you manually set the positioning in nvdia-settings, will this also fix the problem of new windows, run dialogs, etc. popping up across both monitors? I would like to have everything start in one desktop, and the second one essentially act as extra space I can use by dragging windows over to it.

---

### Post by ryanhaigh on 2008-06-13
On my system new windows appear on the display which is currently active (where the mouse was last clicked).

---

### Post by redonwhite on 2008-06-13
> **Banter said:**
> Ok, I figured out what needs to be done to enable "true" dual screens (independent screens) with nvidia.

[back up your xorg config file!]

First, gksudo nvidia-settings in the terminal.
Second, press the detect button to detect your second monitor then press the config button and select the Separate X screen option.
Third, push the 'save to config file' button.
Fourth, press ctrl + alt + backspace to restart X. (your monitor will shut off momentarily)
Finally, you end up with two independent screens. 

The downside is that compiz is super slow when I do this (but just on my laptop screen, not the external monitor), so you may want to disable it. Also you won't be able to drag windows from one monitor to the next (I don't think).


The upside is that you won't end up with one really long desktop spanning two screens at different resolutions . . . and every time you open a new window it appears in the middle of the two screens . . . and when you maximize it fills both screens up . . . alright I'm done.


Any comments? Please let me know what you think!



[B]Hello,  I too have got my dual monitors to work right using this method.  And i also have felt the mad slow down of running 2 X's in order for it to work. The main Monitor was the slower one as well for me.  Im sure turning Compiz off would probably help it run smoother like you suggested.  But i just wish there were a way to Run only One X with Real Dual monitor set up rather then having to run Two X's, having mad slow downs, and not being able to move windows from and too each monitor.
 I love my compiz-fusion.  boo hoo.  Just have to settle with my solo monitor for right now until i learn a way to set it up and not have it slow down my system.  let me know if you find anything.  
[/B]

---

### Post by ryanhaigh on 2008-06-13
> **redonwhite said:**
> Hello,  I too have got my dual monitors to work right using this method.  And i also have felt the mad slow down of running 2 X's in order for it to work. The main Monitor was the slower one as well for me.  Im sure turning Compiz off would probably help it run smoother like you suggested.  But i just wish there were a way to Run only One X with Real Dual monitor set up rather then having to run Two X's, having mad slow downs, and not being able to move windows from and too each monitor.
 I love my compiz-fusion.  boo hoo.  Just have to settle with my solo monitor for right now until i learn a way to set it up and not have it slow down my system.  let me know if you find anything.  


Have you tried the other suggestions in this thread?

---

