---
title: "Computer started booting to a black (blank) screen"
date: 2023-03-17
forum: General Help
---

### Post by Rocky1937 on 2023-03-17
The other day this appeared 'out of the blue'.  The prior day I had done an upgrade to the system 22.02 LTS.  I was able to get the panel to open and to then open Firefox which opened in a 'quarter screen box'.  In addition, the mouse pointer will only appear in the quarter screen box using the normal red pointer...OUTSIDE the box the pointer is represented with a black and white X and is unresponsive when left/right clicking.  Something has changed and after two days of trying to get this corrected...nothing has worked...HELP!!!  Thank God I have a second computer to send this from.

---

### Post by MAFoElffen on 2023-03-18
What is your GPU?
```

sudo lshw -C Video

```

---

### Post by Rocky1937 on 2023-03-18
[COLOR=#333333][FONT=tahoma]     *-display      
description: VGA compatible controller     
product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller     
vendor: Intel Corporation     
physical id: 2     
bus info: pci@0000:00:02.0     
logical name: /dev/fb0     
version: 06     
width: 64 bits     
clock: 33MHz     
capabilities: msi pm vga_controller bus_master cap_list rom fb     
configuration: depth=32 driver=i915 latency=0 resolution=1920,1080     
resources: irq:32 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff     
ralph@ralph-OptiPlex-7020:~$ Rr    [/FONT][/COLOR]

---

### Post by Rocky1937 on 2023-03-18
```
    *-display      
description: VGA compatible controller     
product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller     
vendor: Intel Corporation     
physical id: 2     
bus info: pci@0000:00:02.0     
logical name: /dev/fb0     
version: 06     
width: 64 bits     
clock: 33MHz     
capabilities: msi pm vga_controller bus_master cap_list rom fb     
configuration: depth=32 driver=i915 latency=0 resolution=1920,1080     
resources: irq:32 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff     
ralph@ralph-OptiPlex-7020:~$ Rr    
```

---

### Post by Rocky1937 on 2023-03-18
[COLOR=#333333][FONT=tahoma]     *-display      
description: VGA compatible controller     
product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller     
vendor: Intel Corporation     
physical id: 2     
bus info: pci@0000:00:02.0     
logical name: /dev/fb0     
version: 06     
width: 64 bits     
clock: 33MHz     
capabilities: msi pm vga_controller bus_master cap_list rom fb     
configuration: depth=32 driver=i915 latency=0 resolution=1920,1080     
resources: irq:32 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff     
ralph@ralph-OptiPlex-7020:~$ Rr    [/FONT][/COLOR]

In addition, I am able to run a webcam full screen (Cheese) and am able to adjust an image through Cheese.  But the mouse is still using the X pointer within Cheese rather than the normal red arrow pointer.  I was also able to open Chrome...full screen and it includes my normal red pointer.  What I don't have in that window are the normal screen icons in the upper right corner.  This was the first thing I had noticed the other day when this first started.  I'm now wondering if this started with a Firefox error...???  I currently have Chrome open and Facebook running including having my normal red arrow pointer...all running full screen!!!  This is just crazy!!!

I have just tried to close Chrome and discovered that if I move the cursor to the edge of the screen that the pointer reverts to the black X pointer

---

### Post by MAFoElffen on 2023-03-19
The i915 driver is within the Linux kernel. What happens, if at the Grub2 Boot menu, if you choose the 2nd option (Advanced) and choose an older kernel to boot from?

---

### Post by Rocky1937 on 2023-03-19
I had tried that the other day but ran it again just now...no difference.  I spent some more time and booted from a Windows install...that took an hour or so...hadn't run that since 2020 or so...It booted at last after working through all the up dates and it seemed to run without any problem other than running a bit slow.  At that point I booted back into xbunutu...nothing had changed.  I still think that the problem is tied to this Firefox window that I have been unable to close...even after using the Task Manager to shut it down.  Every time I click on the Firefox link, it opens to that same bad screen.  
My first computer was a IBM PC Junior...but at 85 now, these things just drive me NUTS!!!

---

### Post by MAFoElffen on 2023-03-19
Hmmm. Maybe with things stuck, it might have cause a filesystem error? Just thinking of possibilities.

If you start and at the Grub2 Menu, go to Advanced, then start a recovery menu > Select fsck and see if there are any errors (fix them)...

For my own curiosity, I am not familiar with the "Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller " and how much memory the GPU itself has allocated for it's rendering... Could you please do this, so I can see it?
```

sudo lshw -C video -vvv

```

---

### Post by Rocky1937 on 2023-03-19
Terminal doesn't like that command..even with a copy and  paste

---

### Post by MAFoElffen on 2023-03-20
Sorry. Typo as I was heading out the door for work. Edited last post and here agin:
```

sudo lshw -C video -vvv

```

---

### Post by Rocky1937 on 2023-03-20
I have tried 3 or 4 times to get the fsck to run under recovery...it aborted each time claiming the read/write mode is set to read only and aborts requesting to restart with a reboot.  This experience has really shown me my short term memory has gone to hell!!!  Then adding to the problem with the sick computer and having to transfer info from one computer to the other is a real challenge...getting older is truly not a friend.  I do appreciate your assistance!!!!

---

### Post by MAFoElffen on 2023-03-20
Another way may be to try to run fschk from a liveusb...
```

lsblk

```
Figure out which drive and partition it your drive
```

sudo fsck -p /dev/sdXY

```
Replacing X with the drive and Y with the partition designation...

---

### Post by Rocky1937 on 2023-03-20
OK...interesting...I don't have a live USB...I could create one...In the short term I have switched computers and can live with that outcome.  I do agree with you on the the fact that there was an error in disk writing...it just seems logical.  My question at this point is this a correctable problem?  The computer seems to be somewhat happy to just continue...but without using Firefox.  But,  I would like to correct the problem and to get a full functioning computer back.  Would that require a new hard drive? Or just live live the current situation?  I'm assuming that this error was saved to the hard drive at some point,  rather than a memory artifact and the pointer problem.

---

### Post by MAFoElffen on 2023-03-21
It is fixable. First is fix the filesystem. Offline, without it mounted. It can't be fixed while it is mounted as the root drive.

After that, we need to look at why it did that. It the partition low on space? Is the disk healthy?

I always turn to doing diagnostics to see what happened. With that information, we can make a plan for a solution. Instead of guessing and throwing money and parts at something, hoping. LOL

---

### Post by Rocky1937 on 2023-03-21
OK...What I could do is move the hard drive to my other computer and at that point be able to have access to that drive for the corrective action.  I am currently running a self-testing on that drive...hopefully I can send a copy of that test to you after it completes.  It has already found 24 bad sectors but added that the drive is OK.  It has 4 years 8 months and 16 days of runtime on it.  I have been active on Boinc over the past 15 years or so and for the most part run both computers 24 7.  The test has gotten to 90% complete at this point.

---

### Post by Rocky1937 on 2023-03-22
Well...the test completed but offered nothing to save or print the report...I did take screen shots of the report, but they are of course png files and can't be sent here.  Not sure if there is a work around that might convert the image files to something acceptable here.  I do need to say, that to my untrained eye there was nothing in the report that screamed problem!  I'm thinking that the best thing at this point is to move the problem drive to the other computer and continue testing as an unmounted drive.  Would you agree?

It appears that Firefox has been replaced by Dolphin in that quarter screen...I have no idea when that happen or what I did to make that happen.  That quarter screen has been outside of my control completely!!!  It seems to think that it is the operating system!

---

### Post by MAFoElffen on 2023-03-22
Just thought of something else...

On boot up, when you get to the Login screen, at the panel where you enter the password, in the lower right you will see a gear icon... If you select that, what does it say is selected? Wayland or Xorg? If you select the other option, do you have the same problem?

---

