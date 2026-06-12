---
title: "Log in loop after Nvidia updates"
date: 2016-11-10
forum: General Help
---

### Post by mike-mbcc on 2016-11-10
I am using Ubuntu 16.04, (AMD 64) which has been very stable on my desktop PC, earlier in the week I received a notification concerning new updates, can't remember exactly what they were but do remember one or more of of them being Nvidia updates, decided earlier today to install these updates, everything seemed to install OK with no error messages, closed down the PC, restarted and now I cannot get past the log in screen!
I get no error messages during start, and all appears as previously, but when I try to log in (using the correct password!) it seems to accept the log in but after 3-5 seconds the screen goes blank I hear the bongo sound and I am back to the log in screen again, tried a guest log in, same result.
Also tried Recovery mode (failsafex), not much help, if I choose Try running default setting, screen goes blank showing only x cursor, if I try reconfigure graphics I get two choices, Use Default generic configuration or backed up configuration, none of them do anything, if I click on either I am just returned to the choice dialogue!
Reviewing startup errors (from falesafex) shows nothing!
I can log in using Ctrl/Alt/F1 but do not know what to do from there. 
Looks like the Nvidia update has broken the system, so any ideas how I can take a step back? ( booting from an earlier kernel does not help).

---

### Post by Bashing-om on 2016-11-10
mike-mbcc; Hello;

Let us do suppose the graphic's driver is broke; WE look and see if a driver is loaded.
At the login screen obtain the terminal ( ctl+alt+F1) and log into the system with your credentials.
Now what shows - between code tags for the reply - 
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending what returns, is what we do next.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mike-mbcc on 2016-11-10
From Ctrl+Alt+F1  I get the following:

[FONT=&amp]```
*- display
[/FONT][FONT=&amp]description: VGA compatible controller[/FONT]
[FONT=&amp]product: GF119 [GeForce GT 610][/FONT]
[FONT=&amp]Vendor: NVIDIA Corporation[/FONT]
[FONT=&amp]physical id: 0[/FONT]
[FONT=&amp]bus info: pci@0000:01:00.0[/FONT]
[FONT=&amp]version: a1[/FONT]
[FONT=&amp]width: 64 bits[/FONT]
[FONT=&amp]clock: 33MHz[/FONT]
[FONT=&amp]capabilities: pm msi pciexpress vga_ controller bus_master cap_list rom[/FONT]
[FONT=&amp]configuration: driver=nvidia latency=0[/FONT]
[FONT=&amp]resources: irq: 18 memory: fd000000-fdffffff memory: f0000000-f7ffffff memory: f8000000-f9ffffff ioport: e000 (size=128) memory: fe000000-fe07ffff [/FONT]
```

---

### Post by Bashing-om on 2016-11-10
mike-mbccl Well, well ....

I am at a bit of a loss here, as the card ( GT 610) is identified, the buss is known ( pci@0000:01:00.0 ), and a driver is loaded ( driver=nvidia ).
So, what diver is loaded ?
```

dpkg -l | grep -i ^nvidia

```
Be aware that nVidia recommends the 367 version driver for this card :
[http://www.nvidia.com/download/driverResults.aspx/108586/en-us](http://www.nvidia.com/download/driverResults.aspx/108586/en-us)

Maybe take a look at the log file and see what X thinks ?
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```
As you are at a TTY and no not have the amenities of a terminal emulator - we xfer the file to termbin.
The result here is a URL back in terminal, pass that link back here and we can read the file. - you may also do the same with the dpkg command - .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by mike-mbcc on 2016-11-11
Thanks for the info so far.
The dpkg command you gave returns no output at all!
The result of of the log can be found at:
[http://termbin.com/ly7r](http://termbin.com/ly7r)
Should add that on reflection directly after the first updates (Nvidia) which did not require a restart there was another updates notification with 100MB of security updates (sorry can't remember more) which did require a restart, and it was there the whole problem began, so it may have nothing to do with the Nvidia update at all, sorry if I have mislead you.

---

### Post by Bashing-om on 2016-11-11
mike-mbcc; Humm ...

I do not know what might have happened, but, we sure do not want this:
> 
NVIDIA dlloader X Driver  304.132

Let's see if the easy way to install the nVidia driver will suffice for your use case.
Run terminal commands:
```

sudo rm /etc/X11/xorg.conf

```
To get rid of a "possible" old config file . I do no expect that file to the present, but there is a possibility .
Next is to remove any possible nVidia driver components:
```

sudo apt purge nvidia*

```

And now let us have the system work it's magic, and install the nVidia driver it selects - from what it has to choose from:
```

sudo ubuntu-drivers autoinstall

```

And now to re-boot and see the effect:
```

sudo reboot

```


[INDENT][INDENT]proper care a feeding
[INDENT][INDENT][INDENT]do we have a desktop ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mike-mbcc on 2016-11-11
Thanks! it is working again, I could not use " sudo rm /etc/X11/xorg.conf without a bit of modification, (I got a file does not exist) , but I remembered terminal commands cd and dir so I was able to view etc/X11/ and saw that the file was named xorg.conf.06242014 when I had removed this and run the other terminal commands it installed the correct (367?) driver for graphics and it would appear to be back to normal.
So now a question, I use the desktop PC mainly for editing digital photographs (with Darktable), can I "lock down" this driver in some way so that this cannot occur again?
Don't know if this was anything to do with the cause of the problem, but on reboot I got a message about an incomplete download (flash-plugin), I let the system download this and as mentioned all appears to be back to normal, so thank you once again for your help!

Mike
P.S. Will do a little more testing and mark this post as solved tomorrow.

---

### Post by Bashing-om on 2016-11-11
mike-mbcc; Good deal !

Pleased ya back up and running, you do good work .

As to the graphics driver breaking again .. Most depends on how and from what source you installed the driver .
Most stable/reliable source is the ubuntu software repository - yeah, that driver is not available there .
Next is our trusted PPA :
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Lastly and least - when all else fails - is to install direct from nVidia . Again depending on your experience level . Most times here breakage will occur as the driver is built on the then installed kernel . When the kernel ( and or related libs/files ) get changed .. then the driver must also be re-built . There are things one can do in this instance to ease the pain . But, the cure is not as easy as just installing from our PPA  to begin with.

[INDENT][INDENT]many paths, though
[INDENT][INDENT][INDENT][INDENT]can lead to the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-12
same issue, can't get past login after last updates, been thru the above procedure twice, no luck.

---

### Post by Bashing-om on 2016-11-12
klm3030; Well, well ...

Bear in mind that just because you experience the same symptoms, the cause may be different.
Let us examine a couple of other possibilities, gathering a bit more info along this way.
Show us the outputs of terminal commands:
```

sudo lshw -C display
ls -al .ICEauthority .Xauthority

```

And can you boot to the desktop from the guest account ?

[INDENT][INDENT]fault isolation
[INDENT][INDENT]got to start - somewhere
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ventrical on 2016-11-12
> **klm3030 said:**
> same issue, can't get past login after last updates, been thru the above procedure twice, no luck.

Sometimes depending on the type of hardware used (if it is slightly older) a new kernel update will deprecate the current driver. One way to find out is when booting , hold down shift key and Grub menu will come up. Then choose Advanced and select the previous kernel and see if this solves the problem.

Regards..

---

### Post by klm3030 on 2016-11-13
this is painful, can't cut and paste:

*-display UNCLAIMED
description: VGA compatible controller
product: C^! [GeForce 6150SE nForce 430]
vendor: NVIDIA Corporation
physical id: d
bus info: pci@0000:00:0d.0
version: a2
width:64 bits
clock: 66MHz
capabilities: pm msi vga_controller bus_master cap_list
configuration: latency=0

forgot to tell you can't login as anybody including guest

ls -l shows a .ICEauthority and an .Xauthority file

---

### Post by Bashing-om on 2016-11-13
klm3030l Welp ...

No driver is loaded ; so we got to work to get one installed.
Per: [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
we want the 304 version driver - in a few months that card will no longer be supported by nVidia ; FYI .

Let's try this to install the driver.
```

sudo rm /etc/X11/xorg.conf  #just in case that file "does" exist
sudo apt purge nvidia*
sudo ubuntu-drivers autoinstall

```

reboot and advise on status, got a desktop now ?

Else; we keep digging.


[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-13
OK, I basically followed your procedure, purged nvidia, then rebooted, was able to log in.

then ran the additional drivers program and loaded the nvidia 304 drivers.

all is well at this time.

This sure shakes my faith in installing the updates, cost me two days of downtime.

---

### Post by Bashing-om on 2016-11-13
klm3030; Hey !

Pleased ya got it sorted out.

as to " This sure shakes my faith in installing the updates, cost me two days of downtime." That driver is proprietary, and as such - out of the control of ubuntu. When the proprietary non-ubuntu software breaks, all we can do is try and clean up the mess and re-install the software .

[INDENT][INDENT]some things we just can not help[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-14
all is not well, shut it down last night, same issue this morning, can't login.  So far after following above procedure no luck.

Must be something else to add or remove.

---

### Post by Bashing-om on 2016-11-14
klm3030; Hummm ...

Authorization issue ? I really want to see the complete outputs of terminal commands :
```

ls -al .ICEauthority .Xauthority
dpkg -l | grep -i nvidia

```
and make sure we do not have a driver conflict .

[INDENT][INDENT]here we go again
[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-14
klm@klm-ET1331G:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 klm klm 21990 Nov 14 09:59 .ICEauthority
-rw------- 1 klm klm    56 Nov 14 09:59 .Xauthority




klm@klm-ET1331G:~$ dpkg -l | grep -i nvidia
ii  libcuda1-304                                304.132-0ubuntu0.16.04.2                      amd64        NVIDIA CUDA runtime library

---

### Post by Bashing-om on 2016-11-14
klm3030; Well,

That do say if you are logged onto the system as klm that "you" are authorized to access the desktop.
But if that  all there is for the dpkg command's output, the driver is not installed.

what results :
```

sudo rm /etc/X11/Xorg.conf
sudo apt purge nvidia*
sudo apt install nvidia-304

```

reboot to see the effect
see now

[INDENT][INDENT]where we stand
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-14
I have the same video card and am trying to use the same driver. I've been through the above steps multiple times with no luck.

---

### Post by Bashing-om on 2016-11-14
pizzafarmer_jk; Hello; Welcome to the forum..

Show us what is ,, and we see where we can go:
post back - Between code tags - the outputs of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]just a good place to start
[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-14
yes the driver is not installed, when I install it, can't login.

---

### Post by pizzafarmer_jk on 2016-11-14
> **Bashing-om said:**
> pizzafarmer_jk; Hello; Welcome to the forum..

Show us what is ,, and we see where we can go:
post back - Between code tags - the outputs of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]just a good place to start
[/INDENT]
[/INDENT]



Thanks Bashing-om, here's the output:

```

sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:f4000000-f401ffff


lspci -nnk | grep -iA3 vga
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
    Subsystem: Elitegroup Computer Systems C61 [GeForce 6150SE nForce 430] [1019:2601]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_304


dpkg -l | grep -i nvidia
ii  libcuda1-304                                  304.132-0ubuntu0.16.04.2                      amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                  340.96-0ubuntu0.15.10.1                       amd64        NVIDIA CUDA runtime library
rc  libcuda1-352                                  352.79-0ubuntu0~gpu15.10.1                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-355                                  355.11-0ubuntu0~gpu15.10.2                    amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                    304.132-0ubuntu0.16.04.2                      amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-opencl-icd-304                         304.132-0ubuntu0.16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                               361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver


```

---

### Post by Bashing-om on 2016-11-14
pizzafarmer_jk; Humm ...

What release are you running ?
Maybe a version conflict with nvidia-settings ?
> 
sysop@1404mini:~$ apt list nvidia-settings
Listing... Done
nvidia-settings/trusty [color=red]331.20-0ubuntu8[/color] amd64
sysop@1404mini:~$


be nice
[INDENT][INDENT]if it is that simple
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-14
```

Listing...
nvidia-settings/xenial,now 361.42-0ubuntu1 amd64 [installed,automatic]

```

---

### Post by Bashing-om on 2016-11-14
pizzafarmer_jk; Hey;

> 
nvidia-settings/xenial,now 361.42-0ubuntu1

indicates you are running release 16.04 (xenial). that is a fact ?

As such, if so, I do not know yet what is not taking place with your system either.
Can we get any hints form X's log file ?
Show:
```

cat /etc/X11/xorg.conf 

```

[INDENT][INDENT]stuck between a rock and a hard place
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-14
Correct, I'm on 16.04. Some history on the upgrade to 16.04 - I had this same problem then and fixed it by booting into recovery mode and then installing the video drivers from the Additional Drivers tab in the software settings. That didn't work this time around.

 The xorg.conf file didn't exist, instead there was a file named xorg.conf.failsafe. I had renamed that file earlier on while following other solutions. Here's what was in it:

```

cat xorg.conf.failsafe.bkp
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Hey ..

> **pizzafarmer_jk said:**
> Correct, I'm on 16.04. Some history on the upgrade to 16.04 - I had this same problem then and fixed it by booting into recovery mode and then installing the video drivers from the Additional Drivers tab in the software settings. That didn't work this time around.

 The xorg.conf file didn't exist, instead there was a file named xorg.conf.failsafe. I had renamed that file earlier on while following other solutions. Here's what was in it:

```

cat xorg.conf.failsafe.bkp
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

For sure we do not want to use this file as it is ... loading the vesa driver rather then the nvidia driver.
Now-a-days with the integration of "KMS" (Kernel Mode Setting ) the use of the config file /etc/X11/xorg.conf is depreciated - the kernel does all the discovery - but, if present will be honored . In some cases the config file is needed, but we try not to tell the system what to do and NOT create that file .

In your case here, looks like the driver is installed, and the nvidia driver is in use , and there are no conflicts that I see.
Maybe a config issue in your system account. What results when you access the desktop from the guest account at the login screen ?
If you can not log into the system from the guest account ,,, we will have to dig deep in an effort to find out what is not taking place.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-11-15
klm3030; Hey, hey.

> **klm3030 said:**
> yes the driver is not installed, when I install it, can't login.

Does not give me much to work with ... need the pieces to put this puzzle together.

As is now, let us "assume" that the driver can not build ... and we look to see if the required tools to build are installed;
those tools are the kernel header files.
Show me:
```

dpkg -l | grep linux-

```
and we see what we have to work with ... 
I be slow in mind .. and 1 step at a time kinda guy. I work if not this, then that mind set.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]and the journey will end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-15
I get the same result when I try a guest session, login loop.

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Welp;

> **pizzafarmer_jk said:**
> I get the same result when I try a guest session, login loop.

then we do have driver problems.
We got the tools to build the driver ?
show :
```

dpkg -l | grep linux-

```
and we see where we go from here.

[INDENT][INDENT]there is a way that seems right, but ?
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-15
```


dpkg -l | grep linux-
ii  linux-base                                    4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                1.157.4                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                 4.4.0.47.50                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-31                        4.4.0-31.50                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-34                        4.4.0-34.53                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic                4.4.0-34.53                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36                        4.4.0-36.55                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic                4.4.0-36.55                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38                        4.4.0-38.57                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic                4.4.0-38.57                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-43                        4.4.0-43.63                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                        4.4.0-45.66                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                        4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic                4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.47.50                                   amd64        Generic Linux kernel headers
rc  linux-image-4.2.0-16-generic                  4.2.0-16.19                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic                  4.2.0-34.39                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-35-generic                  4.2.0-35.40                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-36-generic                  4.2.0-36.42                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-38-generic                  4.2.0-38.45                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-41-generic                  4.2.0-41.48                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic                  4.2.0-42.49                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                  4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic                  4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-43-generic                  4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                  4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-16-generic            4.2.0-16.19                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic            4.2.0-34.39                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-35-generic            4.2.0-35.40                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-36-generic            4.2.0-36.42                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-38-generic            4.2.0-38.45                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-41-generic            4.2.0-41.48                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic            4.2.0-42.49                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic            4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic            4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-43-generic            4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic            4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.47.50                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-47.68                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Hummm ...

Well, though a lot of old cruft left laying about, seems the tools are inplace.
But as we pass by, let's clean up.
What kernel are you booting ?
```

uname -r

```
Do we have the operational headroom ?
```

df -h
df -i

```
and cleanup:
```

sudo apt-get autoclean
sudo apt autoremove
sudo apt-get clean
sudo apt update
sudo apt upgrade
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Then again we see what results in installing the nvidia driver.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]expect not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-15
I ran the cleanup that you recommended. Lot's of output. The nvidia driver is currently installed, do I remove it and re-install it?

```


$ uname -r
4.4.0-47-generic

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           383M  6.1M  377M   2% /run
/dev/sda1       291G  156G  121G  57% /
tmpfs           1.9G  300K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           383M   48K  383M   1% /run/user/119
tmpfs           383M     0  383M   0% /run/user/1000

$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             476389     552   475837    1% /dev
tmpfs            489616     753   488863    1% /run
/dev/sda1      19185664 1357907 17827757    8% /
tmpfs            489616       6   489610    1% /dev/shm
tmpfs            489616       5   489611    1% /run/lock
tmpfs            489616      18   489598    1% /sys/fs/cgroup
cgmfs            489616      14   489602    1% /run/cgmanager/fs
tmpfs            489616      22   489594    1% /run/user/119
tmpfs            489616       4   489612    1% /run/user/1000


```

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Uh HUh ..

Looks great for operational overhead. That will not be an issue.
Latest kernel " In component main, is optional. Version 4.4.0.47.50 (xenial) " is installed.

Let's now purge and re-install the driver .
Then we look at the install log for whatever:
```

cat /var/log/nvidia-installer.log

```

[INDENT][INDENT]still look'n for that why
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-15
Just noticed this - the 304 driver should be the correct one for my graphics adaptor but I see that there is a 361 driver installed for the configuration tool. Is that a problem?

```

$ dpkg -l *nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  libgl1-nvidia- <none>       <none>       (no description available)
ii  nvidia-304     304.132-0ubu amd64        NVIDIA legacy binary driver - ver
un  nvidia-common  <none>       <none>       (no description available)
un  nvidia-driver- <none>       <none>       (no description available)
un  nvidia-legacy- <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
ii  nvidia-opencl- 304.132-0ubu amd64        NVIDIA OpenCL ICD
un  nvidia-prime   <none>       <none>       (no description available)
ii  nvidia-setting 361.42-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-vdpau-d <none>       <none>       (no description available)


```

---

### Post by pizzafarmer_jk on 2016-11-15
Hokay, did a purge and re-install of the 304 driver, same results, login loop.

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Naw  ..

The "ii  nvidia-setting 361.42-0ubun" is generic for any version proprietary driver for xenial
What is an issue I think is that "un  nvidia-common"  ; as the nvidia-common package has as a dependency the ubuntu-desktop package.
I do think we want it !
```

sudo apt install nvidia-common
sudo dpkg-reconfigure nvidia-common

```
But I would expect it to be installed by default with the driver build .

Mind ya still look'n for that why not.

---

### Post by pizzafarmer_jk on 2016-11-15
Looks like it installed, didn't say it was already there, but still have the login loop.

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Yuk ...


.ICEauthority and .Xauthority still yours ? 
We got a log file ?
/var/log/nvidia-installer.log.
anything relevant on the GUI log .xsession-errors in your /home ?

If nothing, we can boot to terminal, and from terminal see what the system says when we start the GUI .

At this point about all I know to do.

[INDENT][INDENT]still. got to be a reason
[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-15
klm@klm-ET1331G:~$ dpkg -l | grep linux-
```
ii  linux-base                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                              1.157.4                                       all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.47.50                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-45                      4.4.0-45.66                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic              4.4.0-45.66                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                      4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic              4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.47.50                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-22-generic                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-24-generic                4.4.0-24.43                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic                4.4.0-28.47                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic                4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-22-generic          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-24-generic          4.4.0-24.43                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-generic          4.4.0-28.47                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic          4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic          4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic          4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic          4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.47.50                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-47.68                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by pizzafarmer_jk on 2016-11-15
I'm still owner of .ICEauthority and .Xauthority. There was no nividia installer log.

```

$ cat .xsession-errors
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (GNOME-Flashback:Unity) main process (1967) terminated with status 1
upstart: logrotate main process (1847) killed by TERM signal
upstart: bamfdaemon main process (1910) killed by TERM signal
upstart: Disconnected from notified D-Bus bus

```

---

### Post by Bashing-om on 2016-11-15
pizzafarmer_jk; Yuk;

Just because I do not know what else to do to get us some info,
Boot to terminal:
Reboot, hold down shift until the GRUB boot menu shows. Highlight the Ubuntu entry, press 'E' to edit it. Navigate to the line starting "linux ...", where you see "quiet splash"  remove these terms and all after, and insert systemd.unit=multi-user.target
key combo ctl+x to continue the boot process to TTY1.
Login here with your credentials.

Now start the desktop:
terminal command:
```

systemctl isolate graphical.target

```
Does the system scream and holler ? What errors are reported ? Does the GUI start ?

Be aware That does much more than just start the GUI, it also stops everything that is not a dependency of graphical.target.
In particular is networking . In this environment you are the master and must tell the system to do whatever it is that you want the system to do.

If the GUI does not start, to reboot:
```

sudo reboot

```

[INDENT][INDENT]if I knew better
[INDENT][INDENT][INDENT]I would do different
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-11-15
klm3030; Yuk ...

Again, I do not see a reason here why the module does not build .
As in pizzafarmer_jk 's case, also try and boot to terminal and start the desktop . what results ?

 Again;
[INDENT][INDENT]I just know no better
[/INDENT][/INDENT]

---

### Post by klm3030 on 2016-11-15
I believe the modules do build, it's just that when the nvidia drivers are loaded I (or anybody else) cannot login.

I do not have the drivers installed now because I need to use the computer. 

Don't know if this will help but I also have Mint and Windows loaded and they are working normal.

---

### Post by wildmanne39 on 2016-11-15
If you are using 16.04 it may be secure boot stopping the driver from loading if is is not loading.

Try to disable secure boot in the bios if you have that option then the driver should load if it not already and it sounds like you are not sure.

---

### Post by patrickdug on 2016-11-15
Well, tried everything indicated here, even used the GRUB to select the earlier version to no avail.  The nVidia 304 drivers are installed, I have all permissions but I still can't log in!  Based on the nVidia driver support page, my graphic card is still supported.  What I don't understand here is what does the nVidia driver have to do with logging in?

---

### Post by pizzafarmer_jk on 2016-11-15
I followed the steps to boot to tty1. When I entered the command to start the GUI, there was some text displayed but it was gone before I could read it. The GUI started but I'm in the login loop again.

---

### Post by wildmanne39 on 2016-11-15
They build but probably will not load because of secure boot that is why I said to try to turn it off in the bio's and in the link I am providing it gives another method to do it. Secure boot will stop the driver from loading unless you turn it off or sign the key which is harder to do then just turning secure boot off. Look at the answer that has a green circle it means it is the accepted answer.

Driver and apps will not load in 16.04 and beyond unless secure boot is off or you sign the key for the driver if the key is not built into the kernel which your driver is not.

I had to do this when I help with wireless issues and when I installed virtualbox, there is an issue with it not letting dkms work as well.

Also I used that nvidia for about six years and you can only have one driver installed so make sure to remove all others.
[https://askubuntu.com/questions/761819/nvidi-361-login-loop-ubuntu-16-04-lts](https://askubuntu.com/questions/761819/nvidi-361-login-loop-ubuntu-16-04-lts)

---

### Post by wildmanne39 on 2016-11-15
Please use code tags when posting code.
Thanks

---

### Post by pizzafarmer_jk on 2016-11-16
I have an older system, and the only security option I can find in the  bios is a selection for setup or system. It's currently set to setup  which is supposed to apply security only when accessing setup. I don't  see any other options than that.

I tried installing mokutil as described in the link Wild Man provided, but I get this error when trying to disable validation:

```

$ sudo mokutil --disable-validation
EFI variables are not supported on this system

```

---

### Post by klm3030 on 2016-11-16
Same here exactly.

---

### Post by wildmanne39 on 2016-11-16
> **pizzafarmer_jk said:**
> I have an older system, and the only security option I can find in the  bios is a selection for setup or system. It's currently set to setup  which is supposed to apply security only when accessing setup. I don't  see any other options than that.

I tried installing mokutil as described in the link Wild Man provided, but I get this error when trying to disable validation:

```

$ sudo mokutil --disable-validation
EFI variables are not supported on this system

```What message do you get when you do:
```
sudo modprobe -v nvidia
```

---

### Post by klm3030 on 2016-11-16
insmod /lib/modules/4.4.0-47-generic/updates/dkms/nvidia_304.ko

---

### Post by wildmanne39 on 2016-11-16
Okay, looks like it is not possible for it to be a secure boot issue, so back to your normal guru.

---

### Post by patrickdug on 2016-11-16
Don't have 'secure boot' in my bio.

---

### Post by patrickdug on 2016-11-16
This issue seems to be related to 'older' nVidia graphic cards.  In my case my MB has an integrated chip set.  While my computer is 8 years old, it has a PCI16 slot and I can override the on board graphics by installing a new graphic card, therefore it should get ride of this 304 driver, right? Another option, I just dug through my discarded parts and found a better/more recent MB which I could install and get a new graphics card and power supply for it.

---

### Post by wildmanne39 on 2016-11-16
I take it that you do not want to use the nouveau driver?

---

### Post by patrickdug on 2016-11-16
> **Wild Man said:**
> I take it that you do not want to use the nouveau driver?


Nouveau driver?  I've run through all the steps here and it keeps installing the same driver.  Is there another?

---

### Post by wildmanne39 on 2016-11-16
The nouveau driver is used by default I believe if you do not install a nvidia driver, you can look in your software app and search for it and see if it is installed, remember only one driver or they conflict. I use synaptic for software management so I do not know if you use software center or that new gnome software center but check there.

---

### Post by patrickdug on 2016-11-16
I can't log in to Ubuntu so I can't use anything in there.  I have very little knowledge of Linux/Ubuntu other than I installed it and it runs, well it used to.  If I purge the nVidia drivers and boot up will it install this nouveau driver?

---

### Post by wildmanne39 on 2016-11-16
It should use it as soon as nvidia is purged and you reboot as long as you did not bkacklist the driver.

---

### Post by patrickdug on 2016-11-16
> **Wild Man said:**
> It should use it as soon as nvidia is purged and you reboot as long as you did not bkacklist the driver.


I purged the nVidia drivers per the earlier instructions and the backup copy of the config file, then rebooted.  The first attempt at logging in resulted in a total lock up.  I manually rebooted, logged in, it hiccuped then it worked!  I'm in and everything is running, now I'm rebooting again to ensure it sticks...and it works!  Thanks!

When I ran the 'autoinstall' earlier it installed the 304 nVidia driver.  Looking through the settings I see that it is now using the X.Org X server - nouveau display driver.  So if anybody is still having the log-in lock up issue, try this.

---

### Post by wildmanne39 on 2016-11-16
Glad it worked! Please use thread tools to mark the thread solved.
Enjoy!

---

### Post by patrickdug on 2016-11-16
> **Wild Man said:**
> Glad it worked! Please use thread tools to mark the thread solved.
Enjoy!

well it is solved for me, but I would let the person who originated this thread to indicate it is solved for them as well.  I marked my own thread as solved.
 
Cheers,  Pat...

---

### Post by klm3030 on 2016-11-16
I also was able to purge nvidia and use  Nouveau. However the Chrome browser does not like it and crashes often. Are you saying that this issue can only be fixed by not using the nvidia drivers?  Is anyone else working this problem?

---

### Post by wildmanne39 on 2016-11-16
There may be another way to fix your issue but you will need to post what video card you have and the driver you tried to use. Please start you own thread so it does not get confusing.
Thanks

---

### Post by pizzafarmer_jk on 2016-11-16
Wild Man, I had tried using the nouveau driver earlier on in all of this but it didn't work, just trashed the display. I tried it again just now and was surprised to see that it worked. I'm using the Gnome Flashback desktop with compiz and it displayed all my desktops, wallpaper and all. I was starting to think this might work until I launched Thunderbird and it trashed the display. I had to power it off. When it booted, it trashed the display again right away after login. Thinking maybe compiz was the problem, I tried Gnome Classic but got the same results. Gnome worked at first, but when I logged off to try the Unity desktop, it trashed the display again. It's possible this could work but it's certainly not stable. Any suggestions?

---

### Post by wildmanne39 on 2016-11-16
> **pizzafarmer_jk said:**
> Wild Man, I had tried using the nouveau driver earlier on in all of this but it didn't work, just trashed the display. I tried it again just now and was surprised to see that it worked. I'm using the Gnome Flashback desktop with compiz and it displayed all my desktops, wallpaper and all. I was starting to think this might work until I launched Thunderbird and it trashed the display. I had to power it off. When it booted, it trashed the display again right away after login. Thinking maybe compiz was the problem, I tried Gnome Classic but got the same results. Gnome worked at first, but when I logged off to try the Unity desktop, it trashed the display again. It's possible this could work but it's certainly not stable. Any suggestions?I am not sure how far that driver has progressed in the last couple of years, it did have trouble with compiz.

I used the fall back without compiz it worked great that way. You need to make sure there is no other driver installed do a complete removal of any other drivers or they will conflict.

---

### Post by Bashing-om on 2016-11-16
pizzafarmer_jk; Still here;

And looking over yall's shoulders.
I am not at all conversant with multi-desktops installs. Nor am I comfortable attempting to remove a DE that might be in conflict ( yeah yeah, ain't supposed to happen - but it does ) .
Maybe we can systematically re-install the DEs and see what happens with the open source driver ?
```

ls -al /usr/share/xsessions
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
cat /etc/X11/default-display-manager

```
see what we can

[INDENT][INDENT]finger out
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-17
I think those globals came back blank because I don't currently have a desktop running.

```

$ ls -al /usr/share/xsessions
total 36
drwxr-xr-x   2 root root  4096 Sep  2 08:56 .
drwxr-xr-x 338 root root 12288 Nov 16 16:15 ..
-rw-r--r--   1 root root   236 Feb  9  2016 gnome-classic.desktop
-rw-r--r--   1 root root   207 Aug 22 05:46 gnome.desktop
-rw-r--r--   1 root root   270 Feb 18  2016 gnome-flashback-compiz.desktop
-rw-r--r--   1 root root   278 Feb 18  2016 gnome-flashback-metacity.desktop
-rw-r--r--   1 root root   204 Aug 22 05:47 ubuntu.desktop

$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
 
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm


```

---

### Post by pizzafarmer_jk on 2016-11-17
I currently don't have a desktop running, probably why the globals came back blank.

```

$ ls -al /usr/share/xsessions
total 36
drwxr-xr-x   2 root root  4096 Sep  2 08:56 .
drwxr-xr-x 338 root root 12288 Nov 16 16:15 ..
-rw-r--r--   1 root root   236 Feb  9  2016 gnome-classic.desktop
-rw-r--r--   1 root root   207 Aug 22 05:46 gnome.desktop
-rw-r--r--   1 root root   270 Feb 18  2016 gnome-flashback-compiz.desktop
-rw-r--r--   1 root root   278 Feb 18  2016 gnome-flashback-metacity.desktop
-rw-r--r--   1 root root   204 Aug 22 05:47 ubuntu.desktop

$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
 
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm


```

---

### Post by Bashing-om on 2016-11-17
pizzafarmer_jk; Hummmm ///

System confused as to which display manager to use ? gdm or lightdm ?

With your preference as gnome for the desktop;
How about we set gdm (gnome display manager) as the display manager ?
```

sudo systemctl stop lightdm.service
sudo systemctl start gdm.service
sudo dpkg-reconfigure lightdm

```
Launching a wizard where you may direct that gdm is the manager.

Reboot and let's see if there is an effect to the good.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-17
Well...

```

$ sudo systemctl stop lightdm.service

$ sudo systemctl start gdm.service
Job for gdm.service failed because the control process exited with error code. See "systemctl status gdm.service" and "journalctl -xe" for details.

$ systemctl status gdm.service
&#9679; gdm.service - GNOME Display Manager
   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)
   Active: inactive (dead)

Nov 17 11:48:18 jack-GT5637E systemd[1]: Starting GNOME Display Manager...
Nov 17 11:48:18 jack-GT5637E systemd[1]: gdm.service: Control process exited, code=exited status=1
Nov 17 11:48:18 jack-GT5637E systemd[1]: Failed to start GNOME Display Manager.
Nov 17 11:48:18 jack-GT5637E systemd[1]: gdm.service: Unit entered failed state.
Nov 17 11:48:18 jack-GT5637E systemd[1]: gdm.service: Triggering OnFailure= dependencies.
Nov 17 11:48:18 jack-GT5637E systemd[1]: gdm.service: Failed with result 'exit-code'.
Nov 17 11:48:19 jack-GT5637E systemd[1]: gdm.service: Service hold-off time over, scheduling restart.
Nov 17 11:48:19 jack-GT5637E systemd[1]: Stopped GNOME Display Manager.
Nov 17 11:48:19 jack-GT5637E systemd[1]: gdm.service: Start request repeated too quickly.
Nov 17 11:48:19 jack-GT5637E systemd[1]: Failed to start GNOME Display Manager.

$ journalctl -xe
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit plymouth-quit.service has finished starting up.
-- 
-- The start-up result is done.
Nov 17 11:48:19 jack-GT5637E systemd[1]: gdm.service: Service hold-off time over, scheduling restart.
Nov 17 11:48:19 jack-GT5637E systemd[1]: Stopped GNOME Display Manager.
-- Subject: Unit gdm.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit gdm.service has finished shutting down.
Nov 17 11:48:19 jack-GT5637E systemd[1]: gdm.service: Start request repeated too quickly.
Nov 17 11:48:19 jack-GT5637E systemd[1]: Failed to start GNOME Display Manager.
-- Subject: Unit gdm.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit gdm.service has failed.
-- 
-- The result is failed.
Nov 17 11:48:26 jack-GT5637E dbus[747]: [system] Failed to activate service 'org.bluez': timed out
lines 2509-2531/2531 (END)


```

---

### Post by Bashing-om on 2016-11-17
pizzafarmer_jk; Hummm ...

That sorta changes our perspective .
I look at it like this. As there is gnome-classic.desktop, gnome.desktop, gnome-flashback-compiz.desktop, and gnome-flashback-metacity.desktop installed; then i would think gdm should also be installed.

As it is not .. what else on the system is messed up ?

Let's insure that the system is on a consistent state.
what shows:
```

sudo apt update
sudo apt upgrade
sudo apt autoremove

```

If all at this point looks good,
What now does the package manager think ?
```

sudo apt -f install
sudo dpkg -C

```

And we consider what it will take to get a gnome desktop functional .

[INDENT]just goes to show
[INDENT][INDENT][INDENT]I never wudda thunk it
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-17
```

$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo dpkg -C
$


```

---

### Post by Bashing-om on 2016-11-17
pizzafarmer_jk; Well ..

Pleasantly surprised .

Install gdm ?
what returns;
```

dpkg -l gdm

```

see:
```

apt show gdm

```

[INDENT][INDENT]leastways, that is what I am think'n
[INDENT][INDENT][INDENT]but I have been wrong more than once in my life
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-17
```

$ dpkg -l gdm
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-===============================================
ii  gdm                   3.18.3-0ubuntu2 all             GNOME Display Manager (transitional package)

$ apt show gdm
Package: gdm
Version: 3.18.3-0ubuntu2
Priority: optional
Section: universe/gnome
Source: gdm3
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 69.6 kB
Depends: gdm3
Download-Size: 19.5 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: GNOME Display Manager (transitional package)
 This is a transitional package to ease upgrades to gdm3.
 It can be safely removed.


```

---

### Post by Bashing-om on 2016-11-17
pizzafarmer_jk; Huh ???

Now I am mystified ... package manager is all happy (ii) with the status of gdm, but systemd says no-way I am going to start gdm .

Let's poke at it like so:
```

sudo dpkg-reconfigure gdm

```

Depending, perhaps drop down to the xorg level ??

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-17
Bashing-om, thanks for staying with this. I have to step away for a while though.

```

$ sudo dpkg-reconfigure gdm
$
$ sudo systemctl start gdm.service
Job for gdm.service failed because the control process exited with error code. See "systemctl status gdm.service" and "journalctl -xe" for details.


```

---

### Post by Bashing-om on 2016-11-17
pizzafarmer_jk; Ouch !

But, are we poking at the wrong package ? Maybe I am far behind what is current ?
is this the one we want to poke ?
```
dpkg -l gdm3

```
per: [http://packages.ubuntu.com/search?searchon=contents&keywords=gdm3&mode=exactfilename&suite=xenial&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gdm3&mode=exactfilename&suite=xenial&arch=any)

[INDENT][INDENT]maybe now is better ?
[/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-18
I ran the reconfigure and selected gdm3 and rebooted. The display hung before I got a login prompt.

```

$ dpkg -l gdm3
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-===============================================
ii  gdm3                  3.18.3-0ubuntu2 amd64           GNOME Display Manager
j

$ sudo dpkg-reconfigure gdm3


```

---

### Post by Bashing-om on 2016-11-18
pizzafarmer_jk;  Welp.

Again, not as hoped for. We still do not know the why-fore .
Let's try this and see what hints we get for why the DE is not started.
```

sudo apt install --reinstall gdm3

```
Then If still with issues .. I have in mind to reset the desktop to defaults.
Do we also get a log file ?
what have we :
```

ls -al /var/log/gdm3/

```

[INDENT][INDENT]sure would be nice
[INDENT][INDENT][INDENT]to find some direction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-18
Reinstalled gdm3 and gnome-control-center-data, same as before. There wasn't a log directory for gdm3 but there was for gdm. The files in that directory were all old, none with a recent date and time.

---

### Post by Bashing-om on 2016-11-18
pizzafarmer_jk; Sheeessshhhh .

Still we do not know .

Which desktop of those you have installed is the preferred desktop ?

Let's revert all to defaults:
```

rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf ~/.dmrc -rf

```
reboot and see if "any" of the DEs will now start .

Else we choose one desktop and we concentrate our efforts to start this one .

[INDENT][INDENT]I feel like the blind
[INDENT][INDENT][INDENT]leading the blind[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-19
Ok, deleted those configs and rebooted, still had the screen freeze before I got a login prompt. Just for grins, I changed back to lightdm and rebooted again. I logged into the Ubuntu default desktop (Unity) and then started Firefox. It displayed just fine. Logged out and then back in to each of the desktop options I have, Gnome, Gnome Classic, and Gnome Flashback, all appear to be working. My Compiz settings were all gone of course, so I started putting them back in. I'm back to where I was before now with all my desktops configured and wallpaper set. I've rebooted several times while doing that in case I brought in a problem with one of the settings. So far, so good. I'm going to be cautiously optimistic that it's fixed.

Bashing-om, Wild Man, all others on this thread, thanks for your time and direction. Hope this works for others having this problem.

---

### Post by Bashing-om on 2016-11-19
pizzafarmer_jk; Well, well !

Good news indeed. For my own edification would be good to know how to determine which file(s) were messed up. I can accept that it was " somewhere" in the user space configs of the GUI . 

But;
[INDENT][INDENT][INDENT]all is well that ends well
[/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-19
I guess I spoke too soon. I used it all morning with no problems, but then tried launching Thunderbird. I got a trashed screen and now have the login loop again. I'm going to start removing some of the config files to see if I can figure out what the problem is, but I'm beginning to think I may have to abandon my old hardware and start designing something new.

---

### Post by Bashing-om on 2016-11-19
pizzafarmer_jk; Welp ...

Maybe as it is X2 that starting Thunderbird has resulted in issues, perhaps consider purging Thunderbird and re-install it ?
Pay attention - IF you choose to re-install the app - what errors the system may provide.

leastways
[INDENT][INDENT][INDENT]that is what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by pizzafarmer_jk on 2016-11-20
It really looks like a problem with settings. I deleted all the config files again and no longer have the login loop. I logged into Unity desktop, all good. Logged out and into Gnome Flashback and it was good for a few minutes before I got a trashed display. Rebooted and logged into the Gnome Classic desktop. There have been several instances of garbled wallpaper (just the default Ubuntu wallpaper), but not the entire display. I can select a different workspace to clear that up. So far I have Firefox and Thunderbird running in different workspaces.

I recall that Wild Man mentioned that there were problems with the nouveau driver and compiz. Maybe that's what I'm running into that causes the entire display to go. I'm going to play around with it for a while.

Quick way to see which of those configs have been touched:

```

#! /bin/bash

cd

for i in "gconf" "metacity" "compiz-1" "dmrc"
do
  ls -lsa|grep "$i"
done

for i in "compiz-1" "dconf"
do
  ls -lsa .config|grep "$i"
done


```

---

### Post by spot1984 on 2016-11-20
Still no fix?

I'm having the same issue, see here: [https://ubuntuforums.org/showthread.php?t=2343617&p=13572396#post13572396](https://ubuntuforums.org/showthread.php?t=2343617&p=13572396#post13572396)

~Scott

---

### Post by pizzafarmer_jk on 2016-11-21
No progress with the proprietary driver. I was able to get the nouveau driver to work after deleting the config files but when tried to use the Gnome Flashback desktop with compiz, I wound up in a login loop again. That makes me think the driver isn't the problem and that maybe something is happening to one of the configs. I was able to clear the login loop problem (while on the nouveau driver) by deleting the config files again. I plan to do some testing to see which of these is being touched before I start having problems. Not all of them were rebuilt when I rebooted.

```

rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf ~/.dmrc -rf

```

---

### Post by pizzafarmer_jk on 2016-11-22
What works with the nouveau driver does not work with the nvidia driver. I was reluctant to try it because I was almost back to normal using the nouveau driver, but I re-installed the nvidia driver and tried it again. I was in the login loop and tried removing the config files, but that didn't help this time. The only path that was touched was ~/.config/dconf. I purged the nvidia driver, removed ~/.config/dconf, rebooted, and was able to log into the Gnome Flashback desktop without any problems. The only thing I changed in compiz was the number of workspaces in the general options; no wallpaper this time. It has been stable for the last day now, just not as pretty.

---

### Post by tommy2k10 on 2016-11-22
I had the same problem, but in my case, the automatic update didn't work; I just porged it, rebooted, and it worked!

---

### Post by pizzafarmer_jk on 2017-03-31
I had given up on this since my system was old and it was time to build a new one anyway. After a kernel update on the new system I had another brick, no network or video drivers. The fix for that is here: [https://ubuntuforums.org/showthread.php?t=2356939&highlight=4.8.0-44-generic](https://ubuntuforums.org/showthread.php?t=2356939&highlight=4.8.0-44-generic) . I dug out my old system, hooked it up and tried that fix and it works fine now with the Nvidia driver and no login loop.

---

### Post by wildmanne39 on 2017-03-31
Glad you got it working, would you please put the fix you are referring to into your last post so searches can find it, this is a very long thread and most people will not know what fix you are talking about.
Thanks

---

### Post by pizzafarmer_jk on 2017-03-31
Sure, here it is:

```

sudo apt-get install --reinstall linux-image-extra-4.4.0-57-generic

```

To re-install the Nvidia drivers, I went into System Tools, Preferences, Additional Drivers and selected the proprietary driver from there. Could also do it this way:

```

sudo apt-get install nvidia-304

```

---

### Post by meshica7 on 2017-04-28
This seems to be a big problem.
I am running Ubuntu 16.0.4 LTS on a MacBook Pro
I installed the KDE Plasma de. 
I was getting alerts stating that certain drivers needed to be updated. So I did.
After that..I am stuck in a login loop which only lets me in as a Guest. I tried the Ctl Alt F1 combo to invoke a terminal at the login screen, but nothing happens. And of course trying this as a Guest is not possible either. So I am stuck as to what to do. 
This is the sole OS on my Mac as I did a clean instal. I do have a bootable Seagate drive with OSX that works fine. I really want this MacBook Pro to be Ubuntu exclusive.
So I guess what I am needing to know is how can I access the terminal if the key combo isnt working for me?

I am a newbie to Linux..was usuing Ubuntu years ago and only recently started using it again.

---

### Post by pizzafarmer_jk on 2017-04-29
Can you bring up the GRUB menu by holding the shift key during boot? If so, try booting to a previous generic from the list.

---

