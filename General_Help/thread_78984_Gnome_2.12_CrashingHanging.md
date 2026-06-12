---
title: "Gnome 2.12 Crashing/Hanging"
date: 2005-10-19
forum: General Help
---

### Post by jtwJGuevara on 2005-10-19
Hello all,

Here's my current scenario:

I have Breezy successfully installed.  However, Gnome 2.12 is completely unstable for me.  After logging into Gnome I can operate for approximately 30seconds-3minutes before the desktop environment crashes.  The nature of the problem is that gnome becomes completely unresponsive, including its programs.  The mouse is still working fine, however, all windows, menus and click events do not register and the context senstive icon for the mouse pointer does not change.  This leads me to believe it isn't an Xorg issue since the mouse pointer still works.  I can also sit in GDM for ages without logging in and the system remains stable.  This behavior occurs regardless of the type of session I begin, including failsafe Gnome and failsafe terminal.  The only remedy is to reboot the machine.

It was suggested to me by folks in irc to try a 686 kernel which I did, but to no avail.  It looks as if though my memory and processor utilization always remain minimal through the whole time the system is running as well.  Does anyone have any other suggestions or has anyone seen this type of behavior before?  

Thanks in advance,
Jason

---

### Post by pico303 on 2005-10-19
Sorry this won't be very helpful, but I had the same problem and never found a solution.  Everybody recommended to check the memory (memtest86), check my hard drive, don't use a laptop, etc.  My personal feeling is that it's either something to do with the graphics driver (are you using an NVidia card?) or gcc 4.0.  I've had issues with gcc 4.0 on the Mac, so I wonder if there are troubles on Linux too.

I tried the standard "nv" driver, which worked better than "nvidia."  The driver from NVidia would crash after about 3 minutes, while the xorg "nv" driver lasted for about an hour.  Plus, the Nvidia driver crashed hard, so that not even the mouse pointer would move.  The "nv" driver did what you describe, where I could move the mouse but nothing would run.

My final solution was to roll back to Hoary, which works great.

---

### Post by jtwJGuevara on 2005-10-19
It just so happens I am using an Nvidia card with the nv driver.  I haven't tested  the nvidia driver for 3d support yet since I can't stay in the environment long enough to configure it :)

I have Gentoo up and running on the same machine.  I may give Gnome 2.12 a whirl to see if it has a problem with my hardware. or if it is Ubuntu specific.

---

### Post by ebgreen on 2005-10-19
I had the exact same behavior. In my case, changing the refresh rate seemed to clear it up.

---

### Post by jtwJGuevara on 2005-10-19
The refresh rate in Xorg?  I'll give that a whirl.

---

### Post by jtwJGuevara on 2005-10-19
That didn't work.  I modified xorg.conf to match the same vert and horizontal rates as my working xorg.conf in Gentoo, but the same behavior still persists. :(

I should mentioned however that I started to download two updates from the package manager and they were downloading as Gnome crashed.  However, once the display stopped responding, the harddisk was reading/writing for a brief moment... mostly like corresponding to those updates applying themselves.  As it turns out, the system isn't completely crashing it seems.

---

### Post by Randy Sparks on 2005-10-19
Apols if this sounds obvious but have you tried the Vesa graphics driver? Just try it for a while and see if the crashes clear-up. If so, at least you know what's to blame.

---

### Post by jtwJGuevara on 2005-10-19
I tried them before I checked this post just now and they work.  I'm posting this from Ubuntu as we speak :).

Presently, the problem is somewhat solved so that Gnome is stable.  The problem has to do with the nv driver as well, or possibly any nvidia driver.  My next step is to try the "nvidia" driver with 3d support and see what happens.  This will prove fruitless if I don't have 3d support here and am stuck at 1024x768 resolution.

I'll let you know what I find, so I'll keep this thread active  Thanks everyone who has provided suggestions thus far.

---

### Post by jtwJGuevara on 2005-10-20
Well the problem still isn't solved as I can't even install NVIDIA drivers.  I have a GEFORCE2 GTS, which needs the legacy drivers.  I've followed the directions in Help->Ubuntu 5.10 Starter Guide->Hardware but instead I'm using nvidia-glx-legacy in lieu of the standard drivers.  However, using nvidia-glx-config enable does not update my xorg.conf  Also, nvidia-settings comes up but only displays four or so checkboxes, which I'm sure is incorrect.  

Changing the driver from VESA to nvidia after installing the packages at this point also causes Xorg to not start up.  I tried installing the legacy drivers manually from NVidia direct per the instructions here: [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia) .  But this did not resolve anything either.   

I've tried to manually modprobe the module in, but am receiving this error- 
FATAL: Error inserting nvidia (/lib/modules/2.6.12-9-686/volatile/nvidia.ko): No such device

The nvidia installer completed successfully and nvidia.ko exists quite happily in that directory.  However, I can't figure out what its not detecting.  The hardware manager in Administration -> Device manager detects it.

Of course, this would would explain why using the nvidia driver in xorg.conf doesn't work.

So, I'm still stuck on VESA.  Do you guys have any more guidance?  At the moment I'm going to figure out how to get the nvidia kernel module to load.

---

### Post by jtwJGuevara on 2005-10-21
Solved!

Hopefully at least,

Here's what I did:

I installed the nvidia 7174 drivers from [http://www.nvidia.com/object/linux_display_archive.html]("http://www.nvidia.com/object/linux_display_archive.html")

I then followed the steps detailed in this thread [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia") to install the driver manually.

I then realized I had installed the 686 kernel instead of the 386 kernel.  However, when I ran the nvidia installer, it was installing the nvidia module for my 386 kernel which I wasn't using.  I still had the 386 kernel in my /boot directory, so I edited grub.conf to boot to my 386 kernel instead.  I restarted to use my 386 kernel, hit Ctrl+Alt+F1 to use the command prompt, and killed gdm with /etc/init.d/gdm .  I modprobe'ed nvidia in and it worked.  Restarting gdm at this point enabled the nvidia driver for Xorg.

Life is good for the moment.  I suppose I'll stick with the 386 kernel, but it would be convenient to figure out how to install the nvidia driver against my 686 kernel.  That will be my next task.

Thanks all.

--Jason

---

