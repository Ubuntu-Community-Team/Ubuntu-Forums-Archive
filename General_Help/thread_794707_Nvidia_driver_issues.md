---
title: "Nvidia driver issues"
date: 2008-05-14
forum: General Help
---

### Post by BombaRed on 2008-05-14
Ok, I'm an ubuntu newbie, but I'm learning. I dual boot XP and Ubuntu Hardy.

I have an NVIDIA GeForce FX 5200 graphics card. I can't get out of "low graphics mode" or what ever the specific name is, and my highest screen resolution option is 800x600. When I had everything on XP, I operated at 1280x800 or similar to that. I would really like that back :P

Now, I have these packages installed:
[B]nvidia-kernel-common
nvidia-settings
nvidia-xconfig[/B]

I have tried nvidia-glx, which automatically removes xconfig, and to no avail.

-When I try to access System > Administration > NVIDIA X Server Settings I get: 
> "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

-In an attempt to install the file given to me from NVIDIA's site, I've tried "sudo nvidia-xconfig" in terminal, and get
> Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

and then Ctrl+Alt+Backspace to reset the X server. Didn't do anything.

- I entered "sudo nvidia-xconfig" again, then entered "chmod +x NVIDIA-Linux-x86-169.12-pkg1.run," (which is on my desktop, and opens in text editor if double clicked) and I get:
> chmod: cannot access `NVIDIA-Linux-x86-169.12-pkg1.run': No such file or directory

If I enter "./NVIDIA-Linux-x86-169.12.pkg1.run" I get
> bash: ./NVIDIA-Linux-x86-169.12.pkg1.run: No such file or directory

I have installed bolded packages at the top from the synaptic package manager. I have tried installing each driver that is listed on add/remove, and nothing works.

All tactics I have used to try to fix this are from:

[http://ubuntuforums.org/archive/index.php/t-638119.html](http://ubuntuforums.org/archive/index.php/t-638119.html)

[http://www.overclock.net/nvidia-drivers-overclocking-software/325851-geforce-5200-fx-ubuntu-linux-drivers.html](http://www.overclock.net/nvidia-drivers-overclocking-software/325851-geforce-5200-fx-ubuntu-linux-drivers.html)

---

### Post by BombaRed on 2008-05-14
I hate to bump this, but I really need some answers.

I've been searching around the net, and haven't found much to help me.

---

### Post by OzzyFrank on 2008-05-14
Not sure if I can help, but with me after the Hardy upgrade wrecked my video settings, I grabbed **[COLOR="DarkRed"]EnvyNG[/COLOR]** (it should be at the top of a Google search) and got it to install the nVidia drivers, which eventually fixed things. Give that a try.

---

### Post by EXCiD3 on 2008-05-14
EnvyNG is basically just doing the same thing you were trying to do by compiling the nVidia driver from source. It will also take care of configuring the xserver for you if you chose to let it to. I would recommend trying that first.

---

### Post by dtrot55 on 2008-05-14
Envy is good..but it for some reason messed with my sound drivers..so if you have a Sound Blaster X-Fi watch for that.

---

### Post by Snappo on 2008-05-15
You've got the same problem as me lol...
When i installed on my first harddrive it was fine then i installed on this new one and i am having the same problems.

---

### Post by BombaRed on 2008-05-15
Ok, I've tried EnvyNG.

Auto detect = no fix
Manual select 169.12 = no fix
Manual select 96.43.05 = no fix and it crashes the program once
Manual select 71.86.04 = no fix and it crashes the program once

I tried configuring the setup manually when it prompts me on reboot about the low graphic mode. It gives me the option to choose Nvidia > Geforce fx (generic), but it still doesn't fix anything.

Thanks for those that have given me a hand in this. It's reaching bedtime for me, and I have homework to do. I may just re-install Ubuntu completely. I haven't had it for long, so I won't be losing much. The card worked in the beginning, but didn't allow me to reach the same resolution as i had in XP. At least it was higher than this. Then i let my self-proclaimed "computer expert" friend on here. He claimed he would fix the resolution, and allow it to go higher. Now this.

If it works, I'll give everyone a heads up on it.

---

### Post by PmDematagoda on 2008-05-15
When you get the notice about Low Resolution mode try doing this:-
1) Move to a tty by pressing Ctrl+Alt+F1.

2) Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

3) Reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
selecting "nvidia" as the driver and any other options you may want.

4) Start the X-Server with:-
```
sudo /etc/init.d/gdm start
```

Check if you can get a working X-Server with that.

---

### Post by EXCiD3 on 2008-05-15
You could try going into synaptic and "Completely removing" the packages related to nvidia that you have installed and then reinstalling the graphics driver using System->Hardware Drivers.

I also found this thread, you arent the only one having troubles with the nVidia 5200 [http://ubuntuforums.org/showthread.php?t=792116](http://ubuntuforums.org/showthread.php?t=792116)

---

### Post by BombaRed on 2008-05-15
*I am installing and making updates along with typing this, so it is in order of my actions performed.*

Alright. I did a complete reinstall, and I'm up and running at 1024x768. I have the extra graphics on, and it's running flawlessly. I've also updated the whole system, and installed a few programs.

Now, here's what I picked up on while it installed the working driver:

[B]nvidia-glx-new
nvidia-kernel-common[/B]

were both installed. There was nothing about xconfig or settings. I no longer have the option of System > Administration > NVIDIA X Server Settings. It is simply not there when ubuntu detects the need for drivers and installs them.

I just went into synaptic and installed **nvidia-settings** manually. I went to in System > admin..etc. and now it is working just fine. X Server is there, and I even adjusted my resolution to 1280x1024 under server display configuration.

Thank you all for your help. I hope my little tidbit here can help you out as well.

---

