---
title: "Stubborn/Tricky Driver Problem - Problem Fully  Described"
date: 2008-05-30
forum: General Help
---

### Post by smehmood on 2008-05-30
Hey all,

So I've been trying to get my Dell M1330 (the version with Windows installed by default) to use it's full 1280x800 resolution with the "nvidia" binary driver to no avail. I had it working previously, though through a series of events, it stopped working. I will first explain what I did to get myself in this situation, and then I will list all the symptoms and information I have collected about the current state of my driver problem.

I know there is a lot of information here, so If you want, I'd skip to the "current state" section and see if you can see what's up. I'd appreciate any help or advice.

How I got here
--------------

1. I used to have everything working fine under 7.10, with the driver installed with Envy
2. One day, I tried to set up a projector, and I went in to add a 'Screen 2' I failed to set up the projector properly and gave up. The next time I rebooted, I was at a lower resolution.
3. After fixing my settings, I got it to display the full resolution. However, on restart, it would revert to 1024x768. I would have to go to System > Preferences > Screen Resolution to make it 1280x800. Doing so would work, though it would again revert on restart.
4. I then noticed that the Screen Resolution had an option to make this resolution the default at start up. I checked it.
5. Before I got a chance to see if this was the problem, I upgraded to 8.04. Then the resolution was stuck at 800x600. On boot, it says Ubuntu is in "low graphics mode." I have not been able to fix this.

Current state
-------------

1. If I delete my xorg.conf and xorg.conf file, X successfully detects settings and uses the "nv" driver, and I get 1280x800 resolution. This isn't a good solution because I would like 3D acceleration, and it also doesn't properly detect my touchpad (I have no scroll ability).

2. I have tried re-installing the nvidia driver, using both the "Hardware Drivers" item in System > Administration and EnvyNG. Both still leave me at 800x600.

3. I've tried going to System > Administration > Nvidia X Server Settings to fix things. It tells me that I appear to not be using the "nvidia" driver, and to run nvidia-xconf and restart X (note that the Hardware Drivers screen says I am using the proprietary driver). I do this, it changes my xorg.conf file, yet restarting X doesn't help, and nvidia-settings still says I'm not using the nvidia driver.

4. Note that the option under System > Administration menu no longer has the option that lets me configure screens (resolution, model, etc.) It appears to have been replaced with Nvidia X Server Settings, yet even when I uninstall this, it doesn't reappear. (I may be wrong about this, and the removal of this item might have been a chance from 7.10 and 8.04)

5. I have tried the steps to re Autodetect X Settings, found here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=(resolution)#head-c7979448ab81077f16349d3ca4be7aa5a5a52de2](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=(resolution)#head-c7979448ab81077f16349d3ca4be7aa5a5a52de2)
Curiously, instead of asking me if I want to auto-detect settings, and then letting me press Enter like the site says it will, it instead asks me a question about the kernel framebuffer interface, and then many other questions about keyboard layout and 3 button mouse emulation and the like. This doesn't help.

Relevant Files/Command Outputs
------------------------------

[Current xorg.conf]("http://pastebin.com/f137f5ff")
[xorg.conf that worked before I touched the settings to set up the projecter. Under 7.10]("http://pastebin.com/f7f62444b")
[Output of 'lsmod | grep nvidia']("http://pastebin.com/f3c24c968")
[Output of 'lspsci']("http://pastebin.com/f81eceee")

If anyone thinks its useful, I can post the xorg.conf that gets generated when I don't have an actual xorg.conf file in /etc/X11.

Any help is greatly appreciated.

---

### Post by sdennie on 2008-05-30
You didn't install xserver-xgl at some point did you?  If so, removing it and using nvidia-settings once you completely restart X might fix the problem.  If not, the output of the following commands with the current xorg.conf file you posted might be useful:

```

lsmod | grep nvidia
cat /var/log/Xorg.0.log
cat /var/log/gdm/\:0.log

```

---

### Post by pedro_orange on 2008-05-30
Have you tried:

- Installing nvidia drivers with restricted driver manager
- Ctrl Alt F1
- Then running a: sudo dpkg-reconfigure xserver-xorg
- Explicitly defining the suitable resolutions for your monitor

---

### Post by smehmood on 2008-05-30
I have tried something similar to that before, and I just tried it again.

For some reason dpkg-reconfigure xserver-xorg asks me *nothing* relating to my monitor or screen resolution. From what I read online, and from what you're saying, it sounds like it should be asking me that. Instead, it only asks about keyboard layout and settings, 3 button mouse emulation, and one question at the beginning about using the kernel framebuffer device interface (for which I've tried answering both yes and no).

Anyone have any idea as to why it isn't asking me about monitor settings?

---

### Post by wordatme on 2008-05-30
It appears Ubuntu has long had trouble with nvidia drivers not detecting monitor settings, but I cannot find any online solutions to this problem for version 8.04.  All solutions I have found and tried (there are many!) do not apply because it is obvious 8.04 is just different.  My xorg.conf layout is different from what I see online.  Commands don't work sometimes asking me for password before telling me 'command not found'.

I'm brand new to ubuntu/linux by two days, and I've spent this time trying to figure out what is wrong with my video card/monitor settings/ect.

Everything works fine when I take out the video card.

My experience has been exactly the same as posted above, however I don't have SYSTEM / ADMINISTRATION / Nvidia X server.  I would love to see where I mess with 'nvidia settings'

The more and more I look into this the more confused I get.

---

### Post by pedro_orange on 2008-06-01
Automatically reconfiguirng xserver has been disabled in HH.

See the following bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)

Not sure what to suggest to be honest, I know there are work arounds for GG. Might be an idea to revert to that if the screen resolution is doin your head in.

---

