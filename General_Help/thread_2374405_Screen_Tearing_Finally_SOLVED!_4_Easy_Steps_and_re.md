---
title: "Screen Tearing Finally SOLVED! 4 Easy Steps and reduce Choppiness! and add VSync Too!"
date: 2017-10-15
forum: General Help
---

### Post by markackerman8@gmail.com on 2017-10-15
*** Updated below for Ubuntu 18.04 Bionic Beaver - a even Better Solution, with some tips to minimize Window Dragging Choppiness!

**NOTE: Read Post 7 for a better updated way** which is not Nvidia Driver specific
add this line

> options nvidia-drm modeset=1 
note no driver # needed anymore and to be sure I just upgraded from 390 to 397 and still VSyncing and no tearing WooHoo.

Good News, Ubuntu 17.10 Beta

Screen Tearing has plagued linux/Ubuntu with Nvidia Proprietary Drivers, as we ALL know.

And it is TOTALLY FIXED (for at least this reboot)

All give the long and short of it.

_Short_,
Upgrade to Ubuntu 17.10, ...
and Log into Ubuntu Session ... NOT Gnome Session   (and YES they BOTH use GDM3, and NOT LightDM anymore)
- this cut out 70% of the tearing when moving around Chrome's screen etc. etc.
- then,  PRIME Synchronization on Optimus,  All Tearing GONE, ALL of it!
WooHOO FINALLY! :D

_the  Longer Answer_
Why does Ubuntu's Session work better than Gnome's, and yes they both look EXACTLY the same ... a full Gnome3 Awesome DE.  But it may have something to do with a better xwayland integration (X on top of Wayland) ... Wayland is the future but not quite ready and not ready for Optimus at all YET.

for PRIME Synchronization on Optimus (the lack of synchronization has has plagued optimus Laptops Using Nvidia for 3-4 years)
15/10/17
&#8728; [https://ubuntuforums.org/showthread.php?t=2365449](https://ubuntuforums.org/showthread.php?t=2365449)    .... For Full Instructions
My Notes
            • ```
sudo nano /etc/modprobe.d/zz-nvidia-modeset.conf
```
    &#8728; add:      options nvidia_384_drm modeset=1
           • ```
sudo update-initramfs -u
```
    &#8728; reboot
&#8227; Note: one could also just edit /etc/modprobe.d/nvidia-graphics-drivers.conf on the last line instead on creating a new file. Same affect, the new file method may be slightly more persistent, i.e., an update to nvidia that doesn't up the version #..

• To check - 
           • ```
sudo cat /sys/module/nvidia_drm/parameters/modeset
```
   &#8227; Should say "y" for modeset=1

and can 
           •```
 xrandr --verbose
```
&#8227; 1st. section, (the laptop display), should show PRIME Synchronization: 1 

Great New - SOLVED I hope.

Trying to share the Good News!, Mark :p

---

### Post by markackerman8@gmail.com on 2017-10-24
Easy Peasy - WOW

But here is an update with a simple clean answer, just confirmed it is working after i updated my driver and screen tearing came back, but i remembered I needed to add the specific driver number to the line ....   **IMPORTANT**

```
sudo nano /etc/modprobe.d/zz-nvidia-modeset.conf
```
            add this line to the bottom:      > options nvidia_387_drm modeset=1
Simply make sure the number matches your proprietary driver #,  in my case ...
NVIDIA Driver Version: 387.12 ... therefore you need the > nvidia_387_drm in the line.

```
sudo update-initramfs -u
```
          Reboot

Please say thanks if I helped - Wow So Simple 3 years Later - WHY!!

Anyway Good Luck, Mark:P

---

### Post by slickymaster on 2017-10-24
Thread moved to **General Help** since is 17.10 is already released

---

### Post by mc4man on 2017-10-24
> **markackerman8@gmail.com said:**
> OK So no views - WOW


The "Views" deal in this forum is currently useless, probably better if it didn't exist..
Atm views = replies + 1

Also note this works fine in 16.04.3 image or 16.04.x with the hwe xserver..

---

### Post by JustinJS on 2018-02-19
Found this thread in Google and I made the change now my system is not booting. I get A start job is running for Hold until boot process finished up.

---

### Post by danbroken on 2018-04-24
Works for me! Thanks!! I am searching for this, since that I bought my notebook, 2 years ago. Very Thanks!:guitar:\\:D/:D

---

### Post by markackerman8@gmail.com on 2018-05-01
Update: Here's a Better Solution and with a Non Specific Driver Functionality ... i.e.) no need to modify every time you update your Nvidia Driver!

Get PRIME Synchronization on Optimus 


&#8728; Create a new file in  /etc/modprobe.d/nvidia-drm-nomodeset.conf 
```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf
```

And make sure the following line is present;
[PHP]options nvidia-drm modeset=1[/PHP]

After Update Intramfs,

```
sudo update-initramfs -u
```
 and Reboot

&#8728; To check if it (Synchronization) is NOW set or not set use this command:

```
sudo cat /sys/module/nvidia_drm/parameters/modeset
```

    It should say "y" for modeset=1, which means it is synchronized at 60 fps (I believe) for your Monitor.  ... and All Screen Tearing should be gone
                   for ex. HDMI-1-1, or  eDP-1-1
**Solution** (now for none specific Nvidia Drivers - **AWESOME!**)
DONE!
######################################################

And to Finally get Nvidia Window Dragging almost as SMOOTH as with the nouveaux driver
Here is what I just did in My recent 18.04 re-install, and it was indeed choppy!

The  obvious was set Nvidia to FULL Quality in Nvidia Settings / OpenGL Settings, and ...
in PowerMizer Tab, select "Prefer Maximum Performance", ...

but still not great and I remembered I had not adjusted my swap tendancy to a MUCH lower Value (If you have MORE than enough RAM) 

Swappiness (to Check and it is always defaulted at 60)

```
cat /proc/sys/vm/swappiness
```

&#8227; if 60

```
sudo gedit /etc/sysctl.conf
```

And add these two lines at the bottom and reboot
[PHP]# sharply reduce Swappiness inclination
vm.swappiness=10[/PHP],    and some people set it to 5,1, or even 0!

Reboot, and reset your Nvidia Settings as per above, and Window Dragging is ...

MUCH SMOOTHER!!!!!

Always trying to Help, Mark:o

---

### Post by adamitj on 2018-05-17
> **markackerman8@gmail.com said:**
> Update: Here's a Better Solution and with a Non Specific Driver Functionality ... i.e.) no need to modify every time you update your Nvidia Driver!

Get PRIME Synchronization on Optimus 


&#8728; Create a new file in  /etc/modprobe.d/nvidia-drm-nomodeset.conf 
```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf
```

And make sure the following line is present;
[PHP]options nvidia-drm modeset=1[/PHP]

After Update Intramfs,

```
sudo update-initramfs -u
```
 and Reboot

&#8728; To check if it (Synchronization) is NOW set or not set use this command:

```
sudo cat /sys/module/nvidia_drm/parameters/modeset
```

    It should say "y" for modeset=1, which means it is synchronized at 60 fps (I believe) for your Monitor.  ... and All Screen Tearing should be gone
                   for ex. HDMI-1-1, or  eDP-1-1
**Solution** (now for none specific Nvidia Drivers - **AWESOME!**)
DONE!
######################################################

And to Finally get Nvidia Window Dragging almost as SMOOTH as with the nouveaux driver
Here is what I just did in My recent 18.04 re-install, and it was indeed choppy!

The  obvious was set Nvidia to FULL Quality in Nvidia Settings / OpenGL Settings, and ...
in PowerMizer Tab, select "Prefer Maximum Performance", ...

but still not great and I remembered I had not adjusted my swap tendancy to a MUCH lower Value (If you have MORE than enough RAM) 

Swappiness (to Check and it is always defaulted at 60)

```
cat /proc/sys/vm/swappiness
```

&#8227; if 60

```
sudo gedit /etc/sysctl.conf
```

And add these two lines at the bottom and reboot
[PHP]# sharply reduce Swappiness inclination
vm.swappiness=10[/PHP],    and some people set it to 5,1, or even 0!

Reboot, and reset your Nvidia Settings as per above, and Window Dragging is ...

MUCH SMOOTHER!!!!!

Always trying to Help, Mark:o

That worked flawlessly on my Dell notebook with NVidia GT-730M (Optimus) with Kubuntu 18.04. It fixed also all the icon animations after install nvidia-driver-390 and nvidia-prime packages (after installation they were performing animations too much faster than normal, like there was switched on a turbo button).

Thank you very much!

---

### Post by markackerman8@gmail.com on 2018-05-18
You are VERY Welcome mate!

---

### Post by hickscorp on 2018-06-23
> **markackerman8@gmail.com said:**
> 
```
options nvidia_384_drm modeset=1
```


You sir, are a hero. And I registered this forum just to make sure you knew it.

It might be worth mentioning that it initially didn't work for me, so I tried with different versions:

```

options nvidia_396_drm modeset=1
options nvidia-396-drm modeset=1
options nvidia_drm modeset=1
options nvidia-drm modeset=1

```

And now at least one of them worked - so it won't be too hard for me to find out which one by eliminating them one by one.

A million of kisses all over your special cheeks.

---

### Post by markackerman8@gmail.com on 2018-06-23
Read Post 5 for the none specific version

```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf 
```
add
[HTML]options nvidia-drm modeset=1 [/HTML]

And Woohooo I am your Hero YAYYYY!  You are very welcome

---

### Post by lonerkingtin on 2018-07-12
```
sudo update-initramfs -u

```
After executing this line,



```
update-initramfs: Generating /boot/initrd.img-4.15.0-23-generic
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf: No such file or directory



```

---

### Post by markackerman8@gmail.com on 2018-07-12
> ack@ack-HP-OMEN-Notebook:~$ sudo update-initramfs -u
[sudo] password for ack: 
update-initramfs: Generating /boot/initrd.img-4.15.0-26-generic

no problems with > sudo update-initramfs -u here.

It has nothing to do with nvidia's settings it is simply similar to restarting your machine.

Just trying to help, Mark

---

### Post by markackerman8@gmail.com on 2018-07-21
and just FYI

After a re-install and withscreen tearing again fixed as per above ... even to my own surprise ...

 there was staggering again, ...  The fix ... I even forgot my own advice

As per above setting the SWAP from 60 to 10, and setting Nvidia to Maximum Performance ...

and then restarting to take effect indeed made a big difference for Choppiness !!!  (which is non-existent with the nouveau driver or Intel's)

Just FYI, always trying to help, Mark

---

### Post by WinEunuchs2Unix on 2018-08-06
#9 worked perfectly.

An additional benefit not mentioned. I have three monitors; built in laptop display via Intel iGPU, external TV via nVidia HDMI (hardwired so cannot use if booting via prime-select intel), external TV via Thuderbolt via Intel iGPU.

On a clean install of Ubuntu 16.04.5 nouveau is the default driver with horrid flickering and window artifacts when moved. So I switched to recommended proprietary driver 384.130 but then the external TV connected via Thunderbolt would not turn on during reboot. I had to replug the cable each time.

With `options nvidia-drm modeset=1`
The monitor now starts up automatically on boot!

I'd like to add for modern laptops the nVidia HDMI sound card draws 5 watts so it's turned off during boot. If you want sound through nVidia HDMI then you need to see this post I made today: [https://askubuntu.com/questions/1008599/no-audio-over-hdmi-on-nvidia-geforce-gtx-1050-ti/1062956#1062956](https://askubuntu.com/questions/1008599/no-audio-over-hdmi-on-nvidia-geforce-gtx-1050-ti/1062956#1062956)

TYVMM - Thank you very much Mark.

---

### Post by meambobbo on 2018-08-06
I'm running Pop OS 18.04 LTS on a Dell G3 with a 1050 and these tips worked very well - both the drm modeset and the swap size. Thank you!

---

### Post by markackerman8@gmail.com on 2018-08-20
You are very WELCOME! WooHoo!

---

### Post by flipped-bit on 2018-09-25
Hello, I made this account just to thank this forum for this great solution!

There was one issue though that made me go back to the vanilla teary experience. The problem was that after restarting I noticed that although there was no tearing the desktop wasn't completely smooth, there was some stutter and even after decreasing the swappiness value it didn't stop. 

It was still better in my opinion than the teary mess that i had before. But there was another problem though and it was this one that made me revert the changes, i couldn't use vulkan apps.

I tried to use both RPCS3 and Dolphin-emulator to play some games but they wouldn't boot under vulkan, only if I used OpenGL which has worse performance and adds more stuttering to both emulators.

Although this is a very cool solution it created a problem that was enough for me to go back. I would still like to find a solution to the tearing problem.

In case it helps diagnose the problem, my laptop is a Dell 5577 (16Gb RAM, 512Gb Nvme SSD, Nvidia Gtx 1050, PopOs!18.04.1)

---

### Post by markackerman8@gmail.com on 2018-09-25
You Sir are Very Welcome!

---

### Post by markackerman8@gmail.com on 2018-09-26
And I will Thanks you again,

and I just got a new computer, with Nvidia GTX 1080m, and with this new GPU it acts real well without the VSync, and AND AND ...

I have tried the VSYnc from my own posts that works so well for the past 2 years, BUT it KILLS

ABSOLUTELY KILLS this GTX 1080m,

perhaps its' obvious inboard VSync tool does not like my 
```
sudo gedit /etc/modprobe.d/nvidia-drm-nomodeset.conf
(and adding this that has worked so well for 2 years) 
options nvidia-drm modeset=1

```

Just FYI

aLWAYS TRYING TO HELP, mARK:D

---

