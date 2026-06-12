---
title: "Trouble With Changing My Graphics Drivers To That of My Graphics Card"
date: 2016-12-23
forum: General Help
---

### Post by zorbalorb on 2016-12-23
(Sorry for the long title)

So, I have installed a fresh copy of Ubuntu, but I found out that the graphics had been set to "Gallium on llvmpipe". After a little bit of digging, I found out that my graphics card's driver was an "additional driver", for it was proprietary. Upon changing the driver that was used, the system requested to reboot to complete the installation.

This is where the problem starts.

Upon starting, I was greeted with my usual login screen (but with a very low screen resolution) and when I tried to log in, I was sent back to that same screen. I've tried some methods to cure this that I had found online, but none seem to work for my situation. Any help will be appreciated in this situation.

---

### Post by Bashing-om on 2016-12-23
zorbalorb; Yeah,

Classic example of either a driver not installed or a driver conflict.
What release are you running ?
show :
```

lsb_release -a

```
and what is the hardware we are working with ?
```

lspci -k|grep -iEA5 'vga|3d'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Giving us a target to shoot at.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-23
Running Xenial/16.04.01 LTS

and this is what I got for the second thing:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)    Subsystem: Micro-Star International Co., Ltd. [MSI] GM206 [GeForce GTX 960]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3205



```

My Graphics card is an MSI Geforce GTX 960 4GB
Currently the nouveau driver is being used, as changing it to the nvidiafb driver would cause the problems seen before.

---

### Post by Bashing-om on 2016-12-23
zorbalorb; Well ..

what versions have you tried ?
nVidia recommends the 375 version:
[http://www.nvidia.com/download/driverResults.aspx/112992/en-us](http://www.nvidia.com/download/driverResults.aspx/112992/en-us)
Though 367 may also work equally well.
The 375 version we will have to obtain from our trusted PPA.
Let's make sure of what is presently installed:
```

dpkg -l | grep -i nvidia

```

see where we go
[INDENT][INDENT]from here
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-23
I've tried the NVIDIA Binary Driver-version 367.57 from nvidia-367. As you said, it may work well. I've tried to install that onto the system, but it doesn't let me log into the system after rebooting and sends me back to the log in screen.

after typing that dpkg thing in, this is what I get:
```
ii  libcuda1-304                                304.132-0ubuntu0.16.04.2                      amd64        NVIDIA CUDA runtime libraryii  nvidia-304                                  304.132-0ubuntu0.16.04.2                      amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-current                              304.132-0ubuntu0.16.04.2                      amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                       304.132-0ubuntu0.16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                             361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver



```

---

### Post by Bashing-om on 2016-12-23
zorbalorb; Hey !

And we have the problem identified !
> 
ii  nvidia-current                              304.132-0ubuntu0.16.04.2

Try this:
```

sudo apt purge nvidia*
sudo ubuntu-drivers autoinstall

```
where I do expect the system to choose the 367 version driver to install.

Reboot to see the effect .

[INDENT][INDENT]all better now ?
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-23
Now its stuck at the login screen (at a very low resolution) and logging in brings me back to the login screen with the startup jingle playing. Help?

---

### Post by Bashing-om on 2016-12-23
zorbalorb; Ho Kay ( not );

Let's make sure that "you" are authorized to access your desktop.
from the login screen crl+alt+F1 to gain a console interface.
Login here with your credentials.
what now returns:
```

ls -al .ICEauthority .Xauthority

```
Mine:
> 
sysop@x1604:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 sysop sysop 3768 Dec 23 14:10 .ICEauthority
-rw------- 1 sysop sysop   50 Dec 23 14:10 .Xauthority
sysop@x1604:~$ 

where I am sysop. Is your output the same ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-24
What I get:```

-rw------- 1 zorais zorais 1208 Dec 23 22:43 .ICEauthority
-rw------- 1 zorais zorais 47 Dec 24 10:11 .Xauthority

```
I am zorais
I think that the problem lies in the Nvidia Drivers not being installed properly, as this started to occur right after I installed the drivers. I'm not saying that the drivers themself are bad, but how they get installed onto the system is the problem.

---

### Post by Bashing-om on 2016-12-24
zorbalorb; Uh Huh;

How about we clean things up once more, and try an come up on the open source driver nouveau.
If then we are stable on nouveau, see about what our options are .
```

sudo apt purge nvidia*
sudo apt-get install xserver-xorg-video-nouveau
sudo rm /etc/X11/xorg.conf #I do not expect it to exist, but just in case.
sudo update-initramfs -u

```

Reboot and make sure that nouveau is now available:
```

grep -ri nouveau /etc/modprobe*

```
where you should have no output, just a return to prompt.

We have to establish a base line, something that works -
or find
[INDENT][INDENT]a reason why not
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-24
I managed to get back into my system by running only:
```
sudo apt purge nvidia*
sudo reboot
```

as the Nouveau drivers were already kept on the system

the second command returned nothing.

---

### Post by Bashing-om on 2016-12-24
zorbalorb; Wellll ...

> 
the second command returned nothing. 

Is that in reference to " sudo apt-get install xserver-xorg-video-nouveau" ?
If that is the case, no sass or back-talk is what is expected when there is no problem for the system to report; System doing as told.

Now If the system is fully functional - stable :
what returns :
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers list

```

and we see then what we can do.
[INDENT][INDENT]a story gets told
[/INDENT][/INDENT]

---

### Post by zorbalorb on 2016-12-24
"The second command" means the second code you gave; seperate from the first code-box
```
[COLOR=#000000][FONT=&quot]grep -ri nouveau /etc/modprobe*[/FONT][/COLOR]
```[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

The ubuntu-drivers listed are:
```
intel-microcode
nvidia-367

```

---

### Post by zorbalorb on 2016-12-24
Hold up, i redid the nouveau command and got this:
```
/etc/modprobe.d/nvidia-367_hybrid.conf:blacklist nouveau
/etc/modprobe.d/nvidia-367_hybrid.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-367_hybrid.conf:alias nouveau off
/etc/modprobe.d/nvidia-367_hybrid.conf:alias lbm-nouveau off 
```

---

### Post by Bashing-om on 2016-12-24
zorbalorb; Welp;

In a continued effort to get things cleaned up, and nouveau functional.
Do we still have a nVidia config file ?
```

ls -al /etc/modprobe.d/nvidia-graphics-drivers.conf

```

How is the nouveau driver still blacklisted ?
```

ls -al /etc/modprobe.d/
cat /etc/modprobe.d/blacklist.conf

```

As we do want the system running with the nouvea driver - not the fall back nor not yet a proprietary driver.

We find out what
[INDENT][INDENT][INDENT]and do what it takes
[/INDENT][/INDENT][/INDENT]

---

