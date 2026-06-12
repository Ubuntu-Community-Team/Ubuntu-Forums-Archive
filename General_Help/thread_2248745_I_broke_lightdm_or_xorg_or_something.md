---
title: "I broke lightdm or xorg or something"
date: 2014-10-16
forum: General Help
---

### Post by jamesnicolas on 2014-10-16
This is a long story but I think all the info here might be useful to solving my problem.

I was playing minecraft, and it froze since I overloaded it. Usually I use xkill to kill programs, but since minecraft has control over the mouse, I couldn't. I went into ttys1 and killed java. I went back into ttys7 but everything was still frozen. So I went and killed lightdm since I thought it would restart and show the login screen, because I remembered when trying to install Nvidea drivers I killed something vital like lightdm and it restarted. It didn't, the screen turned black. So I rebooted the computer, but the login screen didn't show up. I then removed lightdm with apt-get and then installed it again and rebooted. It didn't work. I then installed gdm with apt-get and rebooted but it didn't work either. I installed lightdm again but it didn't work again.

I can't reinstall Ubuntu because I have an Apache server running on here and I can't let it have a downtime of over 30 seconds.

How could I identify the problem and fix it?

---

### Post by Bashing-om on 2014-10-16
jamesnicolas; Hi !

As a place to start trouble shooting, do "you" have access to the GUI ?
What returns from :
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Is the system fully updated ?
```

sudo apt-get update
sudo apt-get upgrade

``` So that in the event we need packages to be installed the system is current.

Is the DE installed ?
```

dpkg -l lightdm

```

Then we can look at starting the desk top from terminal and see what errors are generated.

[INDENT][INDENT]hey, it's a thought
[/INDENT][/INDENT]

---

### Post by jamesnicolas on 2014-10-18
> **Bashing-om said:**
> jamesnicolas; Hi !

As a place to start trouble shooting, do "you" have access to the GUI ?
What returns from :
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Is the system fully updated ?
```

sudo apt-get update
sudo apt-get upgrade

``` So that in the event we need packages to be installed the system is current.

Is the DE installed ?
```

dpkg -l lightdm

```

Then we can look at starting the desk top from terminal and see what errors are generated.[INDENT][INDENT]hey, it's a thought
[/INDENT]
[/INDENT]


The first 3 commands you mentioned return:
```
[COLOR=#000000]-rw------- 1 nicolas nicolas 60 Oct 16 18:10 .Xauthority[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
-rw------- 1 nicolas nicolas 4252 Sep 19 21:23 .ICEauthority
[/COLOR][COLOR=#000000]
total 12[/COLOR]drwxr-xr-x  3 root    root    4096 Jul 28 20:29 .
drwxr-xr-x 24 root    root    4096 Sep 29 15:29 ..
drwxr-xr-x 29 nicolas nicolas 4096 Oct 16 18:16 nicolas

```

I don't know if this means I have access to the GUI, but as far as I know, I don't have access to it.

It's updated now. It wasn't before, maybe that fixed things.

When I typed in ```
[COLOR=#222222][FONT=Verdana]dpkg -l lightdm
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]
it returned
[/FONT][/COLOR][FONT=Verdana]
Desired=Unknown/Install/Remove/Purge/Hold[/FONT]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-===============================================================================
ii  lightdm                                               1.10.1-0ubuntu1                                     amd64        Display Manager
```

I don't know if this means the DE is installed or not.

---

### Post by Bashing-om on 2014-10-18
jamesnicolas; Hey ! Looking good;

You do have the required authorizations, and you do have lightdm installed. perhaps all we are looking at is a display manager issue >

Let's see what results when starting the GUI from terminal.
Boot to the grub boot menu -> 'e' key for edit mode -> boot options screen;
Boot parameters screen -> arrow down to the line similar 
> 
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff

replace the terms "quiet splash" - if you have them - with the term "text" - with out the quotes;
key combo ctl+x to continue the boot process to a textual terminal (TTY1).
Log in here with username and password ( no response to the screen when pass word is entered ).

At this terminal, what results:
```

sudo service lightdm start

``` Any errors reported ?

to return to the terminal -> key combo ctl+alt+F1 : return to the GUI -> ctl+alt+F7

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jamesnicolas on 2014-10-18
Okay, I did what you asked but tty7 is still black. When I go back into tty1 it says ```
lightdm start/running, process 1673
```

---

### Post by Bashing-om on 2014-10-18
jamesnicolas; OK,

We have :
> 
but tty7 is still black.

Maybe a graphics driver issue ?
What is the graphics situation ?
post back the outputs - Between Code Tags - of the terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

and let's see if that
[INDENT][INDENT][INDENT]tells us a tale
[/INDENT][/INDENT][/INDENT]

---

### Post by jamesnicolas on 2014-10-18
The first command returns:

```


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
    Subsystem: eVga.com. Corp. Device [3842:3751]
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:3751]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

```

The second command returns

```


  *-display UNCLAIMED
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display UNCLAIMED
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

---

### Post by Bashing-om on 2014-10-18
jamesnicolas; Un Good !

As:
> 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)

The last I was aware, this card is bleeding edge, and there is no other driver available than from Nvidia.

Let me get my mind clear - of other threads - and I will refocus my attention on this and confirm that the state remains.

If you know otherwise, please so advise.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jamesnicolas on 2014-10-18
It's not very new. I think it was released in February. According to this page I think nouveau supports it. [http://nouveau.freedesktop.org/wiki/CodeNames/#nv110familymaxwell](http://nouveau.freedesktop.org/wiki/CodeNames/#nv110familymaxwell)

Currently I am using nvidia's drivers.

---

### Post by Bashing-om on 2014-10-18
jamesnicolas; Hey hey ;

Yepper, agreed, but I still see as "best results" to run the OEM Nvidia driver.
Presently there is no driver loaded:
> 
  *-display UNCLAIMED


I suggest that you re-install the nvidia driver:
per:
> 
Currently I am using nvidia's drivers.

(untrue, as no driver is loaded).

Something broke the Nvidia driver.

[INDENT][INDENT][INDENT]one means to an end
[/INDENT][/INDENT][/INDENT]

---

### Post by jamesnicolas on 2014-10-18
Thank you very much for your time. Unfortunately I don't know how the driver broke so I might not be able to prevent it. It was very strange installing nvidia drivers. I had to apt-get install nvidia-current and then install nvidias's drivers on top of that. The only reason I did that is because no tutorials online explaing how to fix the nvidia.ko error fixed my problem so I tried doing anything.

Anyways, my computer is fixed now so thank you.

---

### Post by Bashing-om on 2014-10-18
jamesnicolas; Yeah ;

I have observed that installing drivers can get to be strange when one departs from the ubuntu package management system.

If all is well at this time:
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and precludes 
others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

