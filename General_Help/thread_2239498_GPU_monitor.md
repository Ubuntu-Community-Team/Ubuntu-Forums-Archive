---
title: "GPU monitor"
date: 2014-08-14
forum: General Help
---

### Post by 700 on 2014-08-14
On the Ubuntu (14.04 LTS) there's a System Monitor tool. This tool is measuring CPU, RAM and Network usage.
Why there's no GPU monitor chart? 
Why there's no temperatures level chart there?
Shouldn't it be like a basic feature?

---

### Post by 3rdalbum on 2014-08-14
a. No, I wouldn't call these "basic features". 99% of the computer-using population doesn't care what temperature the various parts of their computers are running at. I'd consider myself to be part of that 99%. If the temperature is okay, the computer works. If the temperature is too high, the computer shuts down. Displaying a temperature will simply worry much of that 99% of the population: "Oh my god, my CPU is running at 60 degrees celcius! It's overheating!".

You laughed, right? Everybody using Linux will know that 60 celcius is a normal and acceptable temperature for a CPU, right? Wrong. I see threads about it all the time, where people think their computer is overheating.

It's bad enough having a CPU monitor, we occasionally get worried people asking if their CPU will be damaged because they found it running at 100%. However the CPU monitor is useful for a decent percentage of the population so I'd vote to keep it in.

b. A GPU monitor chart might be handy for some, but I wonder whether it would be practical to implement. If you are using a proprietary driver - and I'd bet that anyone concerned about their GPU usage would be - then probably the only way to access that information would be through a secret interface buried in the driver. I don't know about the ATI driver but I don't think the Nvidia control panel can show current GPU load. Perhaps the graphics card itself can't report load?

In the end, Ubuntu is an end-user distro and Gnome (which makes the System Monitor) is an end-user desktop. The things you're asking about aren't exactly things that an average user is concerned with, and including these functions in the System Monitor would probably clutter things up more.

If you want to know temperatures, there are command-line utilities and graphical utilities for displaying those.

---

### Post by grahammechanical on 2014-08-14
When I was using a Nvidia proprietary video driver I could check GPU temperatures and load in the Nvidia Xserver settings manager. If we have the right kind of graphic adapter the load measurement will reflect the load that the GUI is putting on the GPU. It can vary. 

Now I have installed Psensor and System Load Indicator. Both put an app indicator in the Unity top panel. One click and a drop down panel appears showing all the readouts. This is a much better way to keep an eye on motherboard activity then running a utility that will be out of sight when we open applications.

An important thing to remember about Linux and Linux distributions is that they are not controlled by one massive commercial organisation. There is space for other developers to provide utilities. Every Linux distribution is a collection of software projects developed by individual communities.

Regards.

---

