---
title: "Ubuntu lock out"
date: 2016-11-12
forum: General Help
---

### Post by kenmac2 on 2016-11-12
Hi folks,
I have Ubuntu 16.04 running in a dual OS setup with Windows XP.
Last week I downloaded the update that was something to do with Nvidia stuff.
The next day when I tried to boot Ubuntu it asked for the password.
I never used to do this but I entered the Admin password anyway.
It rejected that, and also when I retried.
So, I tried going in as Guest, but same result!
It seems that the Lockout function has been activated somehow.
Is there any way I can bypass the password system and get back in?
Or do I have to reinstall the OS?
Help!

Kenmac

---

### Post by dave-borkowskijr-z on 2016-11-12
[https://ubuntuforums.org/showthread.php?t=2342858](https://ubuntuforums.org/showthread.php?t=2342858)

This worked for me

---

### Post by kenmac2 on 2016-11-12
Thanks Dave,
I'll have a look at the details and see if it helps me.

Kenmac

---

### Post by kenmac2 on 2016-11-13
I tried the Nvidia driver reinstall that did it for Dave but it didn't work for me.
Does anyone else have any suggestions?
As a last resort I'll have to reinstall Ubuntu 16.04.

Kenmac

---

### Post by kenmac2 on 2016-11-13
I have the same problem, which appeared after a Nvidia update.
I reported it in another thread "Ubuntu lockout".
I tried the drivers autoinstalling method but it had no effect.
I'd rather not do a reinstall of Ubuntu, but will do if necessary.

Kenmac

---

### Post by Bashing-om on 2016-11-13
kenmac2; Hello;

Did you check and remove a possible old /etc/X11/xorg.conf file ?
Did you purge drivers prior to attempting the install anew the driver ?
What card do you have ?

[INDENT][INDENT]maybe this
[INDENT][INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wildmanne39 on 2016-11-13
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by kenmac2 on 2016-11-13
I went thru the same steps as MIKE-MBCC.
The report re the display showed
```
 *-display UNCLAIMED
Description:VGA compatible controller
Product: G94 [Geoforce 9600GT] 
```
etc.
I did the driver removal and autoinstall as suggested.
Unfortunately it had no effect on the situation.

Kenmac

---

### Post by Bashing-om on 2016-11-13
kenmac2; Well ,

You want the 340 version driver for that card , 
So what happened, we can look at X's log file and see if we get any hints:
```

cat /var/log/Xorg.0.log

```
and see what is installed for nVidia:
```

dpkg -l | grep -i nvidia

```

There must be a reason that the display is "UNCLAIMED" .

[INDENT][INDENT]look'n to find the why not
[/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-14
I ran both.
The first says there is no such file/directory.
The second gave the following result:
```
ii bbswitch-dkms       0.8-3ubuntu1  i386 Interfacefor toggling the power on NVIDIA Optimus video cards
ii libcuda1-340    340.98-0ubuntu0.16.04.1  i386 NVIDIA CUDA runtime library
ii nvidia-340  340.98-0ubuntu0.16.04.1  i386 NVIDIA binary drive-version 340.98
ii nvidia-opencl-icd-340  340.98-0ubuntu0.16.04.1 i386 NVIDIA OpenCl ICD
ii nvidia-prime   0.8.2  i386 Tools to enable NVIDIA's Prime
ii nvidia-settings  361.42-0ubuntu1  i386  Tool for configuring the NVIDIA graphics driver
```

That seems to indicate that the 340 driver is on board?

Kenmac

---

### Post by Bashing-om on 2016-11-14
kenmac2; Humm ..

Yeah .. 340 is installed .. so begs the question, huh ?

Ok .. what results:
```

sudo modprobe nvidia

```

See what we can do to find out the why the display is UNCLAIMED .

[INDENT][INDENT]gots to be a reason why
[/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-14
I decided to try the purge and autoinstall again.
However, the puige request caused this response:
```
E: Unable to locate package nvidia
```

???

Kenmac

---

### Post by Bashing-om on 2016-11-14
kenmac2; Well ..

Here is a thought .. Are the headers installed to build the driver ?
what returns:
```

dpkg -l | grep linux-

```

And is mode setting aware ?
```

dkms status

```

Though strange,
Has to be a reason
[INDENT][INDENT]installed but not seen
[/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-14
I did the dpkg and got more than a page of text.
No mention of nvidia on what I saw.
Then I ran the status check and it said:
```
nvidia-340, 340.98: added
```

The modprobe resulted in the following:
```
modprobe:ERROR:../libkmod/libkmod-module.c:832  kmod_module_insert_module() could not find module by name='nvidia_340'
modprobe:ERROR: could not insert 'nvidia_340': Unknown symbol in module or unknown parameter (see dmesg)
```

Kenmac

---

### Post by Bashing-om on 2016-11-14
kenmac2; Yuk ;

Look, there is a reason - somewhere , why:
> 
ERROR:../libkmod/libkmod-module.c:832  kmod_module_insert_module() could not find module 

happens.
Most likely , header files to build the module are not present. 
We check for this condition with that dpkg command. You will not see "nvidia" in that list .. but we do want to see that header files for the booting kernel are installed . It is these headers that allow the nvidia module to be built.

So let us prepare to pare that list down and get you some disk space returned .

What kernel are you booting ?
show us:
```

uname -r

```
And is this system fully updated ?
```

sudo apt update
sudo apt upgrade

```
If there are errors, held back packages or anything "unclean" in these outputs, Post these outputs so we know where to direct out efforts .

[INDENT][INDENT][INDENT]rolling our sleeves up;
[INDENT][INDENT][INDENT]we're going to go to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-14
OK. The answer to the 1st is  3.13.0-93-generic.

I ran the update/upgrade commands.
It turns out there were 43 outstanding updates which were duly imported and we are now up to date.
I did notice a couple of items that couldn't be done but I couldn't catch what they were - the screen scrolls thru pretty quickly.

Anyway, I retried the boot procedure, but that hasn't improved.

Kenmac

---

### Post by Bashing-om on 2016-11-15
kenmac2; Sheesshh , Well ....

> **kenmac2 said:**
> OK. The answer to the 1st is  3.13.0-93-generic.

I ran the update/upgrade commands.
It turns out there were 43 outstanding updates which were duly imported and we are now up to date.
I did notice a couple of items that couldn't be done but I couldn't catch what they were - the screen scrolls thru pretty quickly.

Anyway, I retried the boot procedure, but that hasn't improved.

Kenmac

Let's make sure we have the tools on-board to build the driver-module .
Show me:
```

dpkg -l | grep linux-

```
Next we may look at having the available overhead for the system to work in.

[INDENT][INDENT]again, gots to be a reason
[/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-15
I have left out the repeated description lines for clarity.
```

ii linux-base    4.0ubuntu1
ii  linux-firmware     1.157.4
     all    Firmware for Linux kernel drivers
rc  linux-image- 3.13.0.34-generic   3.13.0-34.60
     i386  Linux kernel image for version 3.13.0 on 32 bit x86  SMP

rc  linux-image- 3.13.0.35-generic   3.13.0-35.62 

rc  linux-image- 3.13.0.36-generic   3.13.0-36.63  

rc  linux-image- 3.13.0.37-generic   3.13.0-37.64    

rc  linux-image- 3.13.0.39-generic   3.13.0-39.66  

rc  linux-image- 3.13.0.40-generic   3.13.0-40.69   

rc  linux-image- 3.13.0.43-generic   3.13.0-43.72  

rc  linux-image- 3.13.0.44-generic   3.13.0-44.73  

rc  linux-image- 3.13.0.45-generic   3.13.0-45.74  

rc  linux-image- 3.13.0.46-generic   3.13.0-46.79  

rc  linux-image- 3.13.0.48-generic   3.13.0-48.80  

rc  linux-image- 3.13.0.49-generic   3.13.0-49.83  

rc  linux-image- 3.13.0.51-generic   3.13.0-51.84  

rc  linux-image- 3.13.0.52-generic   3.13.0-52.86  

rc  linux-image- 3.13.0.53-generic   3.13.0-53.89  

rc  linux-image- 3.13.0.54-generic   3.13.0-54.91  

rc  linux-image- 3.13.0.55-generic   3.13.0-55.94  

rc  linux-image- 3.13.0.57-generic   3.13.0-57.95  

rc  linux-image- 3.13.0.59-generic   3.13.0-59.98  

rc  linux-image- 3.13.0.61-generic   3.13.0-61.100  

rc  linux-image- 3.13.0.62-generic   3.13.0-62.102  

rc  linux-image- 3.13.0.63-generic   3.13.0-63.103  

rc  linux-image- 3.13.0.65-generic   3.13.0-65.106  

rc  linux-image- 3.13.0.66-generic   3.13.0-66.108  

rc  linux-image- 3.13.0.67-generic   3.13.0-67.110  

rc  linux-image- 3.13.0.68-generic   3.13.0-68.111  

rc  linux-image- 3.13.0.70-generic   3.13.0-70.113  

rc  linux-image- 3.13.0.71-generic   3.13.0-71.114  

rc  linux-image- 3.13.0.73-generic   3.13.0-73.116

rc  linux-image- 3.13.0.74-generic   3.13.0-74.118

rc  linux-image- 3.13.0.76-generic   3.13.0-76.120

rc  linux-image- 3.13.0.77-generic   3.13.0-77.121

rc  linux-image- 3.13.0.79-generic   3.13.0-79.123

rc  linux-image- 3.13.0.83-generic   3.13.0-83.127

rc  linux-image- 3.13.0.85-generic   3.13.0-85.129

rc  linux-image- 3.13.0.86-generic   3.13.0-86.131

rc  linux-image- 3.13.0.87-generic   3.13.0-87.133

rc  linux-image- 3.13.0.88-generic   3.13.0-88.135

rc  linux-image- 3.13.0.91-generic   3.13.0-91.138

rc  linux-image- 3.13.0.92-generic   3.13.0-92.139

rc  linux-image- 3.13.0.93-generic   3.13.0-93.140

rc  linux-image- 3.2.0.23-generic-pae   3.2.0-23.36

rc  linux-image- 3.2.0.26-generic-pae   3.2.0-26.41

rc linux-image-extra-4.4.0-34-generic   4.4.0-34.53

ii linux-libc-dev:i386               4.4.0-47.68
     Linux kernel header for development
ii linux-sound-base  1.0.25+dfsg-0ubuntu5
     all   base package for ALSA and OSS sound system
ii syslinux-common   3:6.03+dfsg-11ubuntu1
     all   collection of bootloaders(common)
ii syslinux-legacy   2:5.63+dfsg-2ubuntu8
     all   i386 bootloader for Linux/i386 using MS-DOS floppies   

``` 

Next move?

Kenmac

---

### Post by Bashing-om on 2016-11-15
kenmac2; Well.

 when we get around to it, we want to clean and unclutter things.


It has been brought to my attention in another thread ( Wild_Man) that secure boot may play a crucial part in the driver acceptance.
Make sure that secure boot is turned off -

What results now when re-booting ?

If you now purge the driver, and re-install, what happens ?

[INDENT][INDENT]possible and likely
[/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-15
OK, how do we know whether "secure boot" is on or off?
I assume the fact that it asks for a password means it is on?
How do we turn it off?

Kenmac

---

### Post by kenmac2 on 2016-11-16
Re the boot security - I had a look in the Bios.
From what I saw it should not be asking for a password, only when using SETUP.
Both password options were Clear - none required.

Kenmac

---

### Post by Bashing-om on 2016-11-16
kenmac2; Yukkiepoo;

On me. At this point I do not know what else to advise .
We are now above my skill level. Perhaps others here will offer a suggestion.

[INDENT][INDENT]when I do not know
[INDENT][INDENT]I do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kenmac2 on 2016-11-16
Thanks Bashing-Om for your efforts.
I tried the Mokutil method suggested on the other thread, but my system wasn't able to handle it.
Are there any other suggestions folks?
It seems that we are almost at the "last resort" point where we re-install the OS.

Ken Mac

---

### Post by kenmac2 on 2016-11-17
It seems that we have run out of ideas, so this thread remains unsolved.
My Ubuntu has been unaccessable for a week now, so I need to do something to correct things.
I plan to use the boot DVD to reinstall Ubuntu and hope that the same problem doesn't occur after any update action.
It hasn't been a complete loss - I have learnt a few things about the Terminal operations, adding to the knowledge base.
Thanks folks,

Kenmac

---

