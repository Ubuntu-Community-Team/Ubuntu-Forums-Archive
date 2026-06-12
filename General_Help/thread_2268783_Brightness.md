---
title: "Brightness"
date: 2015-03-11
forum: General Help
---

### Post by nefeli2 on 2015-03-11
hello, does anyone know how to fix brightness readjusting itself to minimum. usually happens when i start computer the brightness is minimum and the screen is almost black. i think it might has smth to do with power settings and battery.
thank you :)

---

### Post by Kirboosy on 2015-03-11
Should be a easy enough fix. Go ahead and pull up "System Settings" --> "Brightness & Lock". From there you should be able to configure your settings to how you like them. There may also be some settings under "Power" that will help you out.

Hope that helps!
~Caboose
P.S. I'm assuming you are using Unity Ubuntu 14.04 if not more information about your system would be helpful.

---

### Post by nefeli2 on 2015-03-14
today i had my laptop plugged in with battery on. when battery was charged i unplugged it and brightness immediately went from max to min, making the screen dark. I readjusted it "all settings>brightness and lock" 
I use ubuntu 14.04 LTS
Also i use the battery almost all the time and have the laptop plugged in even though battery is full. maybe that's the problem

---

### Post by pfeiffep on 2015-03-14
I'm not certain if my solution will apply to you ... [have a read]("http://ubuntuforums.org/showthread.php?t=2251752")

---

### Post by nefeli2 on 2015-03-16
i did this:

```
sudo lshw -C display
 
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f6e00000-f6efffff memory:e0000000-efffffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6f00000-f6ffffff
```

and then dowloaded 

**[Intel(R) Graphics Installer for Linux* 1.0.7]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7")**
Released: 11 Nov 2014
Version: 1.0.7
[Release Notes]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7")                                          
[LIST]
[*][Graphics Installer 1.0.7 for Ubuntu* 14.04, 64-bit]("https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb") 
[/LIST]

but, in the software center got error: Wrong architecture 'amd64'
before downloading i also did this as you said
```

wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | sudo apt-key add -

wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | sudo apt-key add -
```

---

### Post by pfeiffep on 2015-03-16
I had to refer to my solution to carefully review the steps! I noticed minor differences in results of the command lshw -C display. I've highlighted  in red below the differences noted:```
pfeiffep@Dell-Studio:~$ sudo lshw -C display
[sudo] password for pfeiffep: 
  *-display               
       description: VGA compatible controller
       [COLOR=#b22222]product: Core Processor Integrated Graphics Controller[/COLOR]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
      [COLOR=#b22222] resources: irq:43 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8[/COLOR])
```
Also please note that results obtained by you contain lines which didn't appear when I ran the command:
> *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6f00000-f6ffffffI wish that I could provide additional guidance, but sadly I cannot. Perhaps others my experienced than I can help!

---

### Post by Kirboosy on 2015-03-16
Sounds like you are running a 32 bit machine if the installer complained about architecture. Try downloading the 32 bit version from the site.

**[Intel(R) Graphics Installer for Linux* 1.0.7]("https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_i386.deb")**

---

### Post by pfeiffep on 2015-03-16
> **nefeli2 said:**
> hello, does anyone know how to fix brightness readjusting itself to minimum. usually happens when i start computer the brightness is minimum and the screen is almost black. i think it might has smth to do with power settings and battery.
thank you :)You may easily validate the 32 vs 64 bit question (of the OS installed not your hardware) using this command which is followed by my output
```
uname -p
x86_64
``` If you've installed the 32 bit OS then it should probably read x86_32

---

### Post by vasa1 on 2015-03-16
See if [http://www.webupd8.org/2014/10/fix-brightness-getting-reset-to-very.html](http://www.webupd8.org/2014/10/fix-brightness-getting-reset-to-very.html) is of any help.

---

### Post by nefeli2 on 2015-03-17
i did understant this: i run the >uname -p   and got i686

But the 32bit version downloaded fine. i hope it works!

O:)

---

