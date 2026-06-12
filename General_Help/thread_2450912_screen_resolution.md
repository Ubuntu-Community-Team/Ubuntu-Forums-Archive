---
title: "screen resolution"
date: 2020-09-23
forum: General Help
---

### Post by christon74 on 2020-09-23
Good morning fellow-Ubunters;) .  I have recently upgraded to 20.04 LTS, but I am not really satisfied with the screen resolution. I am currently using a 19 inches ORION tv set as a monitor (VGA), and the screenshot show you how things look. The settings offer only two options: 1024 x 768 (4:3) or 800 X 600 (4:3). I must say I am not really familiar with all the Xrandr commands. I have read some pages about it, but I think it is wiser not to go it alone and try anything without asking for advice. 
Thanks in advance for any tip.

---

### Post by ajgreeny on 2020-09-23
What is the native resolution of the TV and what computer hardware are you using?

Can you connect with HDMI; it may be much easier than VGA?

---

### Post by ActionParsnip on 2020-09-23
What is the output of:
```

sudo lshw -C display

```
Thanks

---

### Post by agvantibo on 2020-09-23
Try booting to Safe mode, then reboot to normal. It worked for me...

---

### Post by christon74 on 2020-09-23
Many thanks to all of you, ajgreeny, ActionParsnip, agvantibo;)_ The native resolution of this Orion Color TV set is 1440 X 900.
Now here is what lshw -C display gives: ```
   	 	 	 	   sudo lshw -C display
 [sudo] password for christophe:  
   *-display:0 UNCLAIMED      
        description: VGA compatible controller
        product: 4 Series Chipset Integrated Graphics Controller
        vendor: Intel Corporation
        physical id: 2
        bus info: pci@0000:00:02.0
        version: 03
        width: 64 bits
        clock: 33MHz
        capabilities: msi pm vga_controller bus_master cap_list
        configuration: latency=0
        resources: memory:fc000000-fc3fffff memory:e0000000-efffffff ioport:1c70(size=8) memory:c0000-dffff
   *-display:1 UNCLAIMED
        description: Display controller
        product: 4 Series Chipset Integrated Graphics Controller
        vendor: Intel Corporation
        physical id: 2.1
        bus info: pci@0000:00:02.1
        version: 03
        width: 64 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=0
        resources: memory:fc400000-fc4fffff
```

Booting to safe mode? How ? I do not know there is a safe mode with Ubuntu 20.04 LTS? All I know is the recovery option.

---

### Post by NM5TF on 2020-09-24
@chiston74..

open a terminal & type this...
```
cvt 1440 900
```
you should see something like mine...
```
[tommy@tommy ~]$ cvt 1440  900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```
then type this...
```
xrandr --newmode "1440x900_60.00"  [COLOR="#FF0000"]enter the values you got after [COLOR="#00FF00"]Modeline[/COLOR] from the above cvt command[/COLOR]
```
then we need to add the new mode to xrandr  with this...
```
xrandr --addmode  [COLOR="#FF0000"]VGA1[/COLOR] 1440 x900_60.00
``` [COLOR="#FF0000"]NOTE; IF CONNECTED TO THE VGA PORT USE VGA1, OTHERWISE USE THE CORRECT
OUTPUT FOR YOUR DISPLAY[/COLOR]
finally, do this to change resolution to new settings...
```
xrandr --output [COLOR="#FF0000"]VGA1[/COLOR] --mode 1440x900_60.00
```  [COLOR="#FF0000"] NOTE AGAIN, USE CORRECT OUTPUT FOR YOUR DISPLAY[/COLOR]

this is only good for your current session...you will need to add an entry to this directory [COLOR="#FF0000"]/etc/X11/xorg.conf.d/
[/COLOR]
create a new file, name it [COLOR="#FF0000"]10-monitor.conf[/COLOR] it should look something like this...
```
Section "Monitor"
    Identifier "VGA1"[COLOR="#FF0000"](use correct output for your display)[/COLOR]
    Modeline "1440x900_60.00" [COLOR="#FF0000"](insert values from addmode command here)[/COLOR]
    Option "PreferredMode" "1440x900_60.00"
EndSection
```
reboot & see if it works now...

good luck...

tommy

---

### Post by christon74 on 2020-09-24
Good morning Tommy_O:)_ Well, either it's a losing battle or I am hopeless.  Here is what I get : [quote]   	 	 	 	   [FONT=Liberation Sans, sans-serif][SIZE=2]christophe@christophe-ESPRIMO-E5731:~$ cvt 1440 900[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]christophe@christophe-ESPRIMO-E5731:~$ [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]christophe@christophe-ESPRIMO-E5731:~$ xrandr --newmode "1440x900_60.00"[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]xrandr: failed to parse '1440x900_60.00' as a mode specification[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]Try 'xrandr --help' for more information.[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]~$ xrandr --newmode "1440x900_60.00" 106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]xrandr: Failed to get size of gamma for output default[/SIZE][/FONT]

[FONT=Liberation Sans, sans-serif][SIZE=2]xrandr --newmode "1440x900_60.00" 106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]xrandr: Failed to get size of gamma for output default[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]X Error of failed request:  BadName (named color or font does not exist)[/SIZE][/FONT]
  [FONT=Liberation Sans, sans-serif][SIZE=2]Major opcode of failed request:  140 (RANDR)[/SIZE][/FONT]
  [FONT=Liberation Sans, sans-serif][SIZE=2]Minor opcode of failed request:  16 (RRCreateMode)[/SIZE][/FONT]
  [FONT=Liberation Sans, sans-serif][SIZE=2]Serial number of failed request:  19[/SIZE][/FONT]
  [FONT=Liberation Sans, sans-serif][SIZE=2]Current serial number in output stream:  19[/SIZE][/FONT]

[FONT=Liberation Sans, sans-serif][SIZE=2]~$ xrandr --addmode  VGA1 1440 x900_60.00[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]xrandr: unrecognized option 'x900_60.00'[/SIZE][/FONT]
[FONT=Liberation Sans, sans-serif][SIZE=2]Try 'xrandr --help' for more information.[quote]

Anyway, thanks a lot for your time. 
[/SIZE][/FONT]

---

### Post by NM5TF on 2020-09-24
[COLOR="#FF0000"]"failed to get gamma size for output default"[/COLOR]

I have seen this before when Nvidia dropped support for my legacy GPU.....to fix it I had to disable
the Nvidia driver & use the generic 'nouveau" driver.....

since you did not provide any hardware information, could you try this...[COLOR="#FF0000"]you may need to install inxi first.....
[/COLOR]
```
inxi -G
```
this will tell us your hardware & driver in use....

it will look something like mine...
```
[tommy@tommy ~]$ inxi -G
Graphics:
  Device-1: NVIDIA C61 [GeForce 6150SE nForce 430] driver: nouveau v: kernel 
  Display: server: X.Org 1.20.9 driver: nouveau 
  unloaded: fbdev,modesetting,vesa resolution: 1440x900~60Hz 
  OpenGL: renderer: N/A v: N/A 
[tommy@tommy ~]$ 

```

it will be really helpful if you use "code tags" for your answers...that makes it much more readable

use the "adv reply" button, select # from the menu, then insert your answer between the # characters...

tommy

---

### Post by ajgreeny on 2020-09-25
Your "add mode" command at the bottom of post #7 has an extra space after the 1440 so try again without that errant space and it may work

---

### Post by NM5TF on 2020-09-25
> **ajgreeny said:**
> Your "add mode" command at the bottom of post #7 has an extra space after the 1440 so try again without that errant space and it may work

maybe my fault if he just copy/pasted my example in post #6....I also added an extra space in my example add mode line....

Sorry Christon74, I did not see that until AJGreeny pointed it out

tommy

---

### Post by Yellow Pasque on 2020-09-26
> display:0 UNCLAIMED

The intel kernel module ("i915") is not loading. That's bad. Just changing the resolution is not the answer. Even if you could coax 1440x900 out of the generic VESA driver, you would still be without 2D/3D and video decode acceleration.

The first thing to check is that you are not booting into an old, leftover kernel from the previous Ubuntu version (this happens a lot after upgrades for some reason).
```
uname -a
```
If you get a kernel version 5.4.x, that's good. Then see what happens whyen you try to manually load i915
```
sudo modprobe -v i915
```

If uname gives you kernel version < 5.4, then reboot into the correct kernel and remove the old one(s).

---

### Post by christon74 on 2020-10-10
Good morning fellow Ubunters_:D and again thanks to everyone who's answered this thread. I am marking it as solved. Screen resolution is now perfect, without me doing anything. What exactly happened, I do not know. It's some kind of magic.:lolflag:_  I guess that what finally sorted things out was an "apt-update" + "apt-upgrade".

Have a nice week-end all of you.;)

---

