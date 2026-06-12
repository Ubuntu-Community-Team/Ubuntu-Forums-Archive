---
title: "Ubuntu 15.04 freezes"
date: 2015-09-17
forum: General Help
---

### Post by otto8 on 2015-09-17
Hello,

About a month ago I successfully dual booted my Dell GX620 with Ubuntu 15.04 and Win 7, this is my first attempt so I was really happy..... at the time. I’ve been learning alot and have become comfortable using Ubuntu with plans to switch from Windows altogether some time in the future. However there have been some issues I need help with but the one that is troubling me the most  is Ubuntu  freezing up. The only thing I can do is move the mouse.
 
It started about a week and a half ago, it froze up for about 5 minutes than came back. Then about 20 minutes later it froze up again and would not come back so I had to force the shutdown with the power button. I powered back up and Ubuntu started ok but a few days later it happened again forcing me to go through the same process.
 
A few days after the last time I had to force the shutdown several times to get it to come back to life. The only thing I can say that is common every time is that it happens when I’m closing windows. I’ll close Firefox then another window and that’s when it freezes. I think this is all coincidence but that is when it seems to happen.  I have also be getting alot of problem reports which I send.
 
This morning I was closing another window and it froze and then I forced the shutdown but this time I could not get Ubuntu to come back. I tried to start in advanced mode which it did but I don’t know enough to fool around in there so I let it start normally. It did start but the desktop was spread so wide that I could barely get to the quick launch bar but I was able to find the shutdown menu. But again I was met with a blank screen.
 
 I tried starting normally this afternoon just to see if it would, but I got this message “[    0.973366] ACPI PCC PROBE FAILED STARTING VERION 219” and then it stalls forcing another power button shut down.
 
Then I tried using the advanced mode and selected “upstart” which allowed me to get to the desktop but that was it. No quick launch or clock or any other menus only an icon that I put on the desktop to open Libre Calc which it did indeed open.
 
Could someone give me some information about how to get Ubuntu to come back to life and to figure out why it’s freezing so i can fix this?
 
My machine
 Dell GX620 3.4ghz Pentium with 3gb ram.
Onboard video Intel  82945G Express Chipset

Thanks a heap,
Otto

---

### Post by grahammechanical on 2015-09-17
I can tell you this. The message "ACPI PCC Probe Failed" is nothing to do with the problem. And neither is the message "Starting Version 219." These two messages starting appearing in 15.05 during its 26 week development period. It was during the development period that Ubuntu switched from using Upstart as an init system to using SystemD and that is when the message begun appearing. Version 219 is the version of SystemD being loaded.

As for ACPI PCC Probe fail there is this on a mailing list

[http://permalink.gmane.org/gmane.linux.power-management.general/56400](http://permalink.gmane.org/gmane.linux.power-management.general/56400)

Both messages do not show in the development branch of 15.10. Which uses newer kernels than 3.19 and newer versions of SystemD.

As for your real problem I suggest you think about a hardware problem. Overheating? Memory modules not seated properly? CPU overheating?

Regards.

---

### Post by otto8 on 2015-09-17
Thanks for your fast reply,

I will check on the memory sticks and look into the over heating this weekend when I have a little more time but I have to wonder why I am not experiencing any issues on Win 7. Wouldn't it stand to reason that if it was a hardware issue that Windows would also have problems?. Ubuntu was running smoothly up until the problem started and I was using it exclusively until this happened.

Ok..... I'll post back with the results.

Otto

---

### Post by otto8 on 2015-09-18
Ok, I had some time and opened my case to have a look see. While it had some dust in there it wasn't caked on anything (I was half hoping it was) but I blew it all out and reseated the ram. I started up and was able to get to the desktop without issue but that is all I get. It seems to be running normal but with no menus or launcher bar. If I right click I can pull up the settings window and make changes but I can't do anything else. Honestly it seems as though the menus are just not loading......

We are getting aggravated......

---

### Post by v3.xx on 2015-09-18
> and look into the over heating this weekend when I have a little more time but I have to wonder why I am not experiencing any issues on Win 7
My wife's computer will do weird crap when its time to pop the cover and clean it.  My computer is never a problem.

> ACPI PCC PROBE FAILED STARTING VERION 219
As graham has pointed out, this has been going around.
[https://www.google.com/search?client=ubuntu&channel=fs&q=ACPI+PCC+PROBE+FAILED+STARTING+VERION+219&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ACPI+PCC+PROBE+FAILED+STARTING+VERION+219&ie=utf-8&oe=utf-8)

What driver are you running ?

Edit
This is where I end up when searching the chipset.
[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

Not familiar with this driver at all

---

### Post by otto8 on 2015-09-18
I hear ya about your wife's computer. I built ours to be identical but they surely aren't...... odd.

As to the driver I couldn't say which one, it installed when Ubuntu installed plus I'm still quite new to Ubuntu so I wouldn't know where to look. I downloaded that driver from the Win 7 side of this dual boot and since all I can do is see the desktop on Ubuntu I have no idea how I could get it installed.

Thanks very much for your help

---

### Post by v3.xx on 2015-09-18
I'm sure graham will chime back in, he is better at this :)  Till then

Try this .. Press Ctrl + Alt + T

That may get you to a terminal.  If so, enter ..

```
software-properties-gtk
```

And go to the driver tab.

May also try going back to previous kernel.

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

[https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)

---

### Post by otto8 on 2015-09-19
It was late when I was able to get back on Ubuntu so I&#8217;m a little behind in returning&#8230;. Sorry about that.
Anyway I booted to the desktop and was able to open a terminal session. I entered the code and a window popped up that had 5 tabs. #1 Ubuntu Software #2 Other Software #3 Updates #4 Authentication #5 Addition Drivers.
I clicked on Additional Drivers and this is what I found.

Unknown: Unknown
Under that it says &#8220;This device is not working&#8221;
There are 2 other things there the first is unchecked
&#8220;using Processor microcode firmware for Intel CPUs from Intel-microcode&#8221;
The second is checked
&#8220;do not use this device&#8221;
I didn&#8217;t see what I would expect to see for a video driver though the unchecked item might be it. It does seem that I&#8217;m missing something on the video side of things though I am just guessing.
Is this what you were expecting to see?
 
Regards

---

### Post by v3.xx on 2015-09-19
> Is this what you were expecting to see?
Nope, no such luck.  I have not seen this output, but still your on a driver and I would like to know what it is, so please post the output of....

```
lshw -c video
```

---

### Post by otto8 on 2015-09-19
The output is as follows....

WARNING: you should run this program as super-user.
  
*-display:0             
      
description: VGA compatible controller
       
product: 82945G/GZ Integrated Graphics Controller
       
vendor: Intel Corporation
      
physical id: 2
      
bus info: pci@0000:00:02.0
       
version: 02
       
width: 32 bits
       
clock: 33MHz
       
capabilities: vga_controller bus_master cap_list rom
       
configuration: driver=i915 
latency=0
       
resources: irq:16 memory:feb00000-feb7ffff ioport:e898(size=8) 
memory:e0000000-efffffff memory:feac0000-feafffff
  
*-display:1 
UNCLAIMED
       
description: Display controller
       
product: 82945G/GZ Integrated Graphics Controller
       
vendor: Intel Corporation
       
physical id: 2.1
       
bus info: pci@0000:00:02.1
       
version: 02
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list
       
configuration: latency=0
       
resources: memory:feb80000-febfffff

WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


I would have run this program as super user but I don't know how, I must admit.

---

### Post by v3.xx on 2015-09-19
Which takes us back to the same place.

[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

Sorry, but I have no experience with the driver or controller.  Someone will need to assist you on this.

Good luck

---

### Post by otto8 on 2015-09-19
Understood..... thanks for you help I do appreciate it very much.

---

