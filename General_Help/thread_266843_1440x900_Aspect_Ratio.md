---
title: "1440x900 Aspect Ratio"
date: 2006-09-27
forum: General Help
---

### Post by wacole on 2006-09-27
I'm running Nvidia GeForce2 with an Envision 19" widescreen (1440x900 at 60hz) monitor.  I modified xorg.conf to pickup the new resolution and restarted the x server and it worked just fine, filling up the entire screen.

I went out of the room for a few minutes, the screen saver kicked in, and when I returned and hit the space bar to drop the screen saver, the 1440x900 was still there but only about 2/3 of the width of the screen contained the image.  I tried a couple of other resolutions (1280x800, 1280x768,1152x864, etc.) and all of those filled the entire 19" of the screen.  I went back to the 1440xx900 resolution and still had only 2/3rds of the screen filled.

I'd be most grateful for any clues about how to correct this, please.

Thanks very much,

---

### Post by henriquemaia on 2006-09-27
Try running this command from a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the steps presented.

---

### Post by wacole on 2006-09-29
Thanks very much.  I applied the change as you suggested and it worked! ... for awhile.  Then I applied *sudo dpkg-reconfigure -phigh xserver-xorg* and set the high resolution to 1440x900.  And that worked ... for awhile.  Then I reset the resolution to 1280x768 and returned to 1440x900.  That worked the first time I did it and didn't work on subsequent attempts.  

I haven't actually identified the action that is causing the changing of the 1440x900 aspect ratio, but I suspect the screensaver.  So the next step is to see if I can get the resolution back and then turn off the screensaver function and see if that does the job.

Oh BTW, I'm using the Nvidia driver, not the nv driver. Interestingly if I boot from the 5.10 Live-CD (as I have to do on occassion when I exceed the 30 logons without a FS check) the 1440x900 works just fine ... without the nvidia driver.  In fact the xorg.conf file is about as vanilla as one can get.  I'm beginning to think that there is some other issue that I'm not focusing on.

Anyway, if anyone has some suggestions, that would be very welcome.  I'm going to continue to try to get to the bottom of this.

Thanks all.

---

### Post by wacole on 2006-10-03
Update.

After logging on at 1280x768, I decided to take a chance on 1440x900 and tried that resolution.  Same problem; only 2/3rds of the screen was filled.  So I took a chance and logged off (not shutdown or restart) and logged back on and, volia, found that the 1440x900 resolution was retained and filled the screen.

If anyone has an idea of what might be going on here, I be most grateful for your thoughts.

Thanks,

---

### Post by henriquemaia on 2006-10-03
Have you taken a look on refresh rates? There are some howtos on the forums on how to tweak them. You can try that - maybe it will solve this issue.

Check this, for example:

[http://ubuntuforums.org/showthread.php?t=83973&highlight=howto+refresh+rate](http://ubuntuforums.org/showthread.php?t=83973&highlight=howto+refresh+rate)

Read also my posts on the thread, as they may help you further ahead if you get in trouble.

Good luck.

---

### Post by wacole on 2006-10-04
Thanks very much for the link.  I'll read and digest this and report back.  Really appreciate the help.

---

### Post by wacole on 2006-10-11
After checking out the various strategies that have been suggested, I'm ashamed to admit, but here it is anyway, that the problem appears to be the electronics in the monitor.  When the screen is 2/3rd size and the monitor power is cycled off and then on, the screen returns to normal size **every time.** Time to contact Envision.

Thanks for all your suggestions.  I learned a lot.

---

### Post by fragos on 2006-10-11
There's never shame in sharing the truth.  We've all now learned something.

---

### Post by henriquemaia on 2006-10-12
> **wacole said:**
> After checking out the various strategies that have been suggested, I'm ashamed to admit, but here it is anyway, that the problem appears to be the electronics in the monitor.  When the screen is 2/3rd size and the monitor power is cycled off and then on, the screen returns to normal size **every time.** Time to contact Envision.

Thanks for all your suggestions.  I learned a lot.

At least the troubleshooting was worthwhile. Good luck with your monitor.

---

### Post by wacole on 2006-10-20
Well, after all that it isn't a "bad" monitor.  Plugged the monitor into another computer running W2K and had none of the screen size problems that I experince on the Linux box. 

On the Linux box if the screen sized is reduced and I cycle the power 2 to 3 times, eventually screen size will return to normal.  Why would powering the monitor on and off fix the problem?  Is this something to do with power management?

---

### Post by fragos on 2006-10-20
Perhaps it's your video card or on-board video chip set.  Diagnosing flaky hardware from a distance can be difficult and this is such a case.  I hate to suggest you spend money on a new video card when we're in trial and error mode.

---

### Post by wacole on 2006-10-22
Thanks for the idea.  The mobo is a K7 socket with AMD751/756 chipset for which I don't see Linux chipset drivers on the AMD site (could be the problem?).  I'll run some diagnostics on the video which is a PNY w/a GeForce2/GTS chipset.

---

### Post by discord on 2006-10-22
> **wacole said:**
> Thanks for the idea.  The mobo is a K7 socket with AMD751/756 chipset for which I don't see Linux chipset drivers on the AMD site (could be the problem?).  I'll run some diagnostics on the video which is a PNY w/a GeForce2/GTS chipset.

The first time i turned my 1650x1080 display on it didnt use the whole monitor. I looked at the monitor manual and reset it and now it works fine. I think it didnt work because previous I had used a non standard mode. Is your screensaver running at a different resolution than your desktop? What does your xorg.conf look like?

---

