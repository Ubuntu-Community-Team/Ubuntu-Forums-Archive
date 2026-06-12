---
title: "How can i change how my linux computer works"
date: 2020-07-10
forum: General Help
---

### Post by enzolakes on 2020-07-10
Hi I was wondering if i can do something to make ubuntu change my  audio output when i connect HDMI. I'm a linux beginner and i dont know  how to really use the console. I hope you understan what im trying to  say. Greetings from Argentina.

---

### Post by yetimon_64 on 2020-07-10
No need for the console/terminal if you have pulseaudio volume control (package name: pavucontrol) installed.
As an example of its use I have attached a screenshot, it shows xmms2 running (currently paused but still active).
[ATTACH=CONFIG]286428[/ATTACH]
To change the audio output for xmms2 I click on the output button and a drop down menu appears from where I can select hdmi or stereo or in my case a combination of the 2 running together as I have enabled a combined sink as well. This will only change the output for that particular applications stream (xmms2) though.

To set an output sink as default output you can go to the outputs tab in pavucontrol and click the relevant "set as fallback" button (the green circle with a tick mark in it) for the output you want used by default. In the attached screenshot I only show my default (HDMI) output for selecting a fallback  device...
[ATTACH=CONFIG]286429[/ATTACH]

As you mention the console I am wondering if you are actually wanting to do this from the terminal/console. 
I assumed you want to do this from the desktop, I can give terminal commands for this IF you are doing this from the console.
Let me know if this answer is applicable to your needs.

Good luck, 
Regards, yeti.

---

### Post by enzolakes on 2020-07-10
Thanks dude, that was really helpful and it worked perfectly. By the way, how do yo enable a combination output? I try to do that a time ago and i didnt find a way to do it, so maybe you'll solve two of my problems hahaha. Thanks again!

---

### Post by yetimon_64 on 2020-07-10
> **enzolakes said:**
> Thanks dude, that was really helpful and it worked perfectly. By the way, how do yo enable a combination output? I try to do that a time ago and i didnt find a way to do it, so maybe you'll solve two of my problems hahaha. Thanks again!

Good to hear that worked :).

For setting up a combined sink I do a bit of scripting with the pacmd command to set mine up here due to spending a lot of time on a console only boot. My combined sink is automatically enabled on the console using bashrc and the scripting and carries over into any desktop I start up.

Use this next method for normal GUI usage ;)...

For more "normal" GUI usage I have the packages "paprefs" and "pasystray" installed and can set up a combined sink by using the icon in the [s]notification area[/s] **(Edit**: actually it is the "indicator applet") of my DE and selecting "Configure local sound server"...
[ATTACH=CONFIG]286430[/ATTACH]

From the window that pops up using "Configure local sound server" choose the "Simultaneous output" tab and tick the check box there "Add virtual output device for for simultaneous output on all local sound cards". That should set you up using a more standard method than I use ...
[ATTACH=CONFIG]286431[/ATTACH]

Regards, yeti.

---

