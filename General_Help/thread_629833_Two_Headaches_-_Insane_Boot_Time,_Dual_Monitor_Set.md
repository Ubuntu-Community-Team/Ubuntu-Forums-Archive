---
title: "Two Headaches - Insane Boot Time, Dual Monitor Setup"
date: 2007-12-02
forum: General Help
---

### Post by sunkssss on 2007-12-02
I'm pretty new to Ubuntu - I installed a dual boot onto my notebook yesterday. But even before booting up after finishing the install, I had a problem.

1) It takes about 5 minutes to get to the login screen. I have a feeling this might be related to a hardware issue with one of my USB ports (which is one reason I decided to install Ubuntu, because Windows was giving me a headache over the whole problem). Although there is no device attached to my USB ports, in Windows there is a device error detected. Once Ubuntu is actually started, I get no such headache, but as it is booting up it is having trouble resolving my issue with the USB ports. I guess the only way I see of fixing this is to somehow force the system to ignore the error, but I don't have the slightest idea how to do this. Any creative ideas? 

I'm also having an issue with setting up a dual monitor setup.

2) Maybe I haven't installed the proper drivers, but I can't quite get my display settings to work properly on startup. One problem is with my notebooks main screen, when I start up a window will appear saying that my device settings aren't properly configured, and i will choose to continue the startup but only with a resolution of 800x600 (but the native resolution is 1024x768). Once I'm logged in I'm able to change my settings, log out, and then it's changed to 1024x768. Maybe I haven't acquired the right drivers?

Then I'm also having trouble getting my external monitor to be recognized. I have been able to get a signal to it, but it's stuck at 800x600 on both the external monitor and my notebook's screen. I'm unable to set the monitor to it's native 1680x1050 and my notebook to 1024x768. Again, it's probably because I don't have the right drivers set up. The external monitor is a Westinghouse 22" widescreen, LCM-22w3. 

My notebook is an IBM Thinkpad T40, graphics are Radeon Mobility 7500. 

Thanks for any help you can offer, and again I'm unfortunately somehwhat clueless as to Ubuntu "lingo" so the simpler you can make it sound, the better. I'm trying to learn what I can, it just takes a while, and mostly it's trial and error.

---

### Post by irish_flu on 2007-12-02
You *might* be able to disable your USB ports in the BIOS or "Setup" screen that you get to by hitting  DEL/F12/F2/ etc as soon as the machine starts to boot.

Sorry I can't be more specific, you'll have to research the BIOS options for your specific notebook.

---

### Post by sunkssss on 2007-12-02
Wouldn't that also mean I couldn't use either of my USB ports? I'd like to avoid that, as they do in fact work... just, they seem to be causing my slow boot. I just want to put a "patch" over the issue so it doesn't affect the system startup.

---

### Post by irish_flu on 2007-12-02
Well, again that depends on the BIOS of your specific machine.  You might be able to disable only one "bank" of them, or something.

Does this happen before Ubuntu even begins to start up?  As in, do your think your computer might be looking at your USB port to try and detect a hard drive that it might wish to boot from?

If that is indeed the case, your BIOS might allow you to simply disable the option of *booting* from USB.  I'm not sure that'll do you any good (again, I'm not sure where the hang is) but it might be worth a shot.

---

### Post by sunkssss on 2007-12-03
I was able to go into my BIOS and disable boot from USB, but that made no difference. It appears to purely be a problem with loading Ubuntu - as it tries to detect my hardware it gets an error, which loops several times and then continues.

Any ideas about my graphics settings, why I  can't setup dual display? Now I'm unable to turn on desktop effects, although I had been able to enable them earlier.

---

### Post by psycho5 on 2007-12-03
Disabling USB boot won't fix the problem because BIOS checks for boot options even before grub loads. You need to "turn off" your USB port. If you have no option as such, I suggest you try updating your BIOS. 

As for your other problem. You need to read this thread: 

[http://ubuntuforums.org/showthread.php?t=122094](http://ubuntuforums.org/showthread.php?t=122094)

To update your BIOS just boot into BIOS and see what company's BIOS you are using and then look for an update through the net. You would probably need to do that through windows. There should be  a way to update through Ubuntu, but I don' t know how.

---

### Post by sunkssss on 2007-12-03
Unfortunately I already do have the updated BIOS for my computer. I'm going to try reinstalling Ubuntu and see what happens.

---

### Post by sunkssss on 2007-12-03
In case it helps, I think I saw what the problem is:

221.096000 USB 4-4: device descriptor read/64, error -110

alternately...

USB 1-1: device descriptor read/64, error -71

these two lines repeat for about 5 minutes straight. Any ideas what it means?

---

### Post by Slick.N on 2007-12-04
I've got a "me too" on the boot time. I'm getting error -110 messages, usually about 6 of them, before I reach the splash screen.

What do they mean?

---

### Post by p_quarles on 2007-12-04
The bootup times in these cases sound kind of extreme, so I'm not sure if these tutorials will solve the problem, but I've found them both very useful:
[http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html](http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html)
[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+time](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+time)

By making some of the suggested changes, I was able to reduce boot time (power button > login screen) from about a minute to 20 seconds. 

In any case, the sysv-rc-conf program allows you pretty fined grained control over what loads during the boot process. Just be careful -- read the tutorial and know what you're doing before making changes.

---

### Post by pointone on 2007-12-04
Try changing /sys/module/usbcore/parameters/old_scheme_first to Y (default N).

---

### Post by Slick.N on 2007-12-04
> **pointone said:**
> Try changing /sys/module/usbcore/parameters/old_scheme_first to Y (default N).

Thanks for the suggestion, pointone. 

gedit won't let me open that file though.

---

### Post by sunkssss on 2007-12-05
I'm unable to access it either. I tried that link, psycho5, but was unable to find what I needed. I still can't configure my graphics drivers. I would like to believe a drivers pack exists somewhere that has what I need. I'm almost considering trying to install feisty fawn since I've seen some places that suggest the problem didn't exist there...

---

### Post by pointone on 2007-12-05
Use vim or nano instead of gedit.

---

### Post by sunkssss on 2007-12-05
So I've been able to solve most of my graphics issues, I think. I used a program called Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)), uninstalled my ati drivers, then reinstalled the newest version. I now am able to have visual effects turned all the way up, and my screen resolution stays steady. However, I haven't been able to get the right screen configuration for my external 22" monitor...

---

### Post by Slick.N on 2007-12-06
Unscientifically, I seem to have cured by boot problems. I have a new 7 port USB hub, and the system boots fine if my Memory stick is *not* plugged in.

---

### Post by SigmundFreud on 2007-12-06
> **Slick.N said:**
> Unscientifically, I seem to have cured by boot problems. I have a new 7 port USB hub, and the system boots fine if my Memory stick is *not* plugged in.
I was about to point to the hub. The -117 error is a sign that the USB hub has power problems. In my case what solved it was not to use all of its four slots (but at the most three).

---

