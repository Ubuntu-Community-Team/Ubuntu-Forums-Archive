---
title: "No login screen"
date: 2014-09-30
forum: General Help
---

### Post by ariel8 on 2014-09-30
After i boot up my computer the xubuntu loading screen comes on after that nothing appears except a flashing grey line(i forgot what is its name XD) the only thing i have access to is the altgr+sysrq which most of it is disabled
i cant do anything except emergency sync which doesn't seem to do anything...
what should i do?

---

### Post by Bashing-om on 2014-09-30
ariel8ariel8; Hi !

What led up to this turn of events ? Have you installed any new software ? Did maybe do an update to currently installed application cause this ?

In any event, let's see if we can get you to a terminal. If so then we can find out what is taking place.

Reboot, as soon as the boot splash screen clears, depress and hold the right -shift- key -> grub boot menu.
With the latest kernel highlighted press the 'e' key for edit mode -> boot options screen.
Arrow down and across to the terms "quiet splash" and replace these terms with the term 'text' with out the quotes.
Key combo ctl+x to continue the boot process to a textual terminal (TTY1); Login here with username and password - no response to the screen when pass word entered, normal -> security reasons.

What results from terminal command:
```

startx

```

IF you can start the GUI - so advise us - be advised the key combos ctl+alt+F1 will return you to the terminal interface, and key combo ctl+alt+F7 to go back to the GUI.

[INDENT]finding out what
[INDENT][INDENT][INDENT]condition the condition is in
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ariel8 on 2014-09-30
> **Bashing-om said:**
> ariel8ariel8; Hi !


What led up to this turn of events ? Have you installed any new software ? Did maybe do an update to currently installed application cause this ?


In any event, let's see if we can get you to a terminal. If so then we can find out what is taking place.


Reboot, as soon as the boot splash screen clears, depress and hold the right -shift- key -> grub boot menu.
With the latest kernel highlighted press the 'e' key for edit mode -> boot options screen.
Arrow down and across to the terms "quiet splash" and replace these terms with the term 'text' with out the quotes.
Key combo ctl+x to continue the boot process to a textual terminal (TTY1); Login here with username and password - no response to the screen when pass word entered, normal -> security reasons.


What results from terminal command:
```

startx

```


IF you can start the GUI - so advise us - be advised the key combos ctl+alt+F1 will return you to the terminal interface, and key combo ctl+alt+F7 to go back to the GUI.
finding out what
condition the condition is in



the resuLt of startx gives an error of no screen detected
I tried to install drivers after the reboot it brought me to a terminal like login, then i looked up on how to fix it, found a way of using a backup of an older settings file for xorg and after that i rebooted my PC agin and that's where it started. If you are wondering yes, i did back up the settings file that was used.
i cant do alt+ctrl+f1, no response

---

### Post by Bashing-om on 2014-09-30
ariel8; OK ;

So now we know a bit, and have a direction to work toward .

Boot back to the terminal.
What returns now from terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To save you some typing, in the 'lshw' output all we are interested in is the contents of the configuration line:
> 
configuration: driver=radeon latency=0

In my case .

Let's consider what it will take to replace that graphics driver.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-01
> **Bashing-om said:**
> ariel8; OK ;

So now we know a bit, and have a direction to work toward .

Boot back to the terminal.
What returns now from terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To save you some typing, in the 'lshw' output all we are interested in is the contents of the configuration line:

In my case .

Let's consider what it will take to replace that graphics driver.
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]

It dosnt say radon as the driver;
```
configuration: driver=fglrx_pci latency=0
```
What do i do now?

---

### Post by Bashing-om on 2014-10-01
ariel8; Yeah,

We are working on it .. So far we know from that last output you are running an ATI proprietary driver for graphics.
We need to know for which ATI card.
Post back the out put of:
```

lspci -nnk | grep -iA3 vga

``` as we consider replacing the (broken ??) driver.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-01
> **Bashing-om said:**
> ariel8; Yeah,

We are working on it .. So far we know from that last output you are running an ATI proprietary driver for graphics.
We need to know for which ATI card.
Post back the out put of:
```

lspci -nnk | grep -iA3 vga

``` as we consider replacing the (broken ??) driver.
[INDENT][INDENT]hey, it could happen
[/INDENT]
[/INDENT]

```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D]  [1002:1714]
       Subsystem: Acer Incorporated [ATI] Device [1025:061d]
       Kernel driver in use: fglrx_pci
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI audio [Radeon HD 650D and 6400G-6600G series] [1002:1714]
```
that's the output

---

### Post by Bashing-om on 2014-10-01
ariel8; Great !

That relieves concerns that the card is not supported.

Is there a reason that you are running with a proprietary driver ? .. I have in mind to purge the present driver(s) and install the open source driver.
See then if you can activate the GUI desk top.

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by alodeiro on 2014-10-01
Hi all,  try add nomodeset at the grub startup line and then install the video driver graphically  :-\"

---

### Post by ariel8 on 2014-10-01
> **Bashing-om said:**
> ariel8; Great !

That relieves concerns that the card is not supported.

Is there a reason that you are running with a proprietary driver ? .. I have in mind to purge the present driver(s) and install the open source driver.
See then if you can activate the GUI desk top.
[INDENT][INDENT]it's a thought
[/INDENT]
[/INDENT]

I have no problems switching drivers, can you gove me the command(s) to install it?

---

### Post by Bashing-om on 2014-10-01
ariel8; Sure !

^^ alodeiro's advise has good merit, I however do prefer to use the terminal making sure all is cleaned up and installed correctly.
Terminal commands:
-where '#" denotes a comment and need not be entered.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates  ##removes all the proprietary driver files
sudo apt-get install dkms  ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon  ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core  ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg  ## just that, make the operating system forgets the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u  ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Reboot to see the effect.
I fully expect you to boot to the GUI.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-01
> **Bashing-om said:**
> ariel8; Sure !

^^ alodeiro's advise has good merit, I however do prefer to use the terminal making sure all is cleaned up and installed correctly.
Terminal commands:
-where '#" denotes a comment and need not be entered.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates  ##removes all the proprietary driver files
sudo apt-get install dkms  ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon  ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core  ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg  ## just that, make the operating system forgets the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u  ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Reboot to see the effect.
I fully expect you to boot to the GUI.[INDENT][INDENT]it could happen
[/INDENT]
[/INDENT]


thank you, i am trying this right now
edit: did not work:/
it said something about disabled speech

---

### Post by Bashing-om on 2014-10-02
ariel8; Humm;

Maybe more at play here than meets the eye.
> 
edit: did not work:/
it said something about disabled speech

Conveys little information. We need to see these complete results in the context you got them. Code tags ! and transfer the command and what is returned in the terminal back to the forum thread:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Let's make sure the open source driver is not blacklisted, to where the kernel will not load it.
Post back the outputs of:
```

ls -al /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf

```
You say:
> 
I tried to install drivers after the reboot it brought me to a terminal like login, then i looked up on how to fix it, found a way of using a backup of an older settings file for xorg and after that i rebooted my PC agin and that's where it started.


Moving the config files and replacing the driver should have for sure resolved that situation. so NOW what is ?
Again, from the "configuration line" what driver is loaded  - if any -?
```

sudo lshw -C display

```

If we see no problems, next we look at how the DM gets started.

[INDENT][INDENT]we do fault isolation
[INDENT][INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-04
> **Bashing-om said:**
> ariel8; Humm;

Maybe more at play here than meets the eye.

Conveys little information. We need to see these complete results in the context you got them. Code tags ! and transfer the command and what is returned in the terminal back to the forum thread:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Let's make sure the open source driver is not blacklisted, to where the kernel will not load it.
Post back the outputs of:
```

ls -al /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf

```
You say:


Moving the config files and replacing the driver should have for sure resolved that situation. so NOW what is ?
Again, from the "configuration line" what driver is loaded  - if any -?
```

sudo lshw -C display

```

If we see no problems, next we look at how the DM gets started.[INDENT][INDENT]we do fault isolation[INDENT][INDENT][INDENT][INDENT]to restoration
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

ls -al /etc/modprobe.d:
```

alsa-base.conf             blacklist-firewall.conf          blacklist-oss.conf                dkms.conf               iwlwifi.conf
blacklist-ath_pci.conf    blacklist-framebuffer.conf    blacklist-rare-network.conf   fbdev-blacklist.conf  mlx4.conf
blacklist.conf               blacklist-modem.conf          blacklist-watchdog.conf        fglrx.conf               vmwgfx-fbdev.conf

```
cat /etc/modprobe.d/blacklist.conf:
```

blacklist evbug

blacklist usbmouse
blacklist usbkbd

blacklist eepro10

blacklist de4x5

blacklist eth1394

blacklist snd_intel8x0m

blacklist snd_aw2

blacklist i2c_i801

blacklist prism54

blacklist bcm43xx

blacklist garmin_gps

blacklist asus_acpi

blacklist snd_pcsp

blacklist pcspkr

blacklist amd76x_edac

```
sudo lshw -C display
```

   *-display
          description: VGA compatible controller
          product: BeaverCreek [Radeon HD 6530D]
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 1
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
          compatibilities: pm pciexpress msi vga_controller bus_master cap_list rom
          configuration: driver=fglrx_pci latency=0 
          resources: irq:18 memory:c0000000-cfffffff ioport:f000(size:256) memory:fef00000-fef3ffff

```

---

### Post by Bashing-om on 2014-10-04
ariel8; Hey !

Post #11 still refers. Presently we still see:
> 
configuration: driver=fglrx_pci latency=0 
 a proprietary drivers. Post #11 will remove the proprietary driver and install the open source drive "radeon".

Step through post #11 and advise if problems -> go through the 'blacklist' file in that event.

We are working toward changing the graphics driver.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-04
> **Bashing-om said:**
> ariel8; Hey !

Post #11 still refers. Presently we still see:
 a proprietary drivers. Post #11 will remove the proprietary driver and install the open source drive "radeon".

Step through post #11 and advise if problems -> go through the 'blacklist' file in that event.

We are working toward changing the graphics driver.
[INDENT][INDENT]ain't no step for a stepper
[/INDENT]
[/INDENT]

still no gui, only a different font. should i follow post #13 now?

---

### Post by Bashing-om on 2014-10-04
ariel8; Small steps, small steps;

My post #2 refers,
In order to get a GUI established we must first get a terminal. In this terminal we are going to execute some commands to remove the graphics driver (post #11) .. and install it's replacement driver 'radeon'.
To do post #11 we must get a terminal - in one shape, fashion, form or another.

Try post #2 and advise on results of activating a terminal.

Small steps
[INDENT][INDENT]will get the job done
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-04
> **Bashing-om said:**
> ariel8; Small steps, small steps;

My post #2 refers,
In order to get a GUI established we must first get a terminal. In this terminal we are going to execute some commands to remove the graphics driver (post #11) .. and install it's replacement driver 'radeon'.
To do post #11 we must get a terminal - in one shape, fashion, form or another.

Try post #2 and advise on results of activating a terminal.

Small steps[INDENT][INDENT]will get the job done
[/INDENT]
[/INDENT]

here are the errors that i get:
```

(EE)
Fatal server error
(EE) no screens found(EE)
(EE)
Please consult the The X.Org foundation support
          at http://wiki.x.org
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE)Server terminated with error (1). closing the log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error


```

---

### Post by Bashing-om on 2014-10-04
ariel8; Umph;

As before, you could get a terminal, now you can not ??? And seems now X will not start !
What has transpired to make this turn of events ?

Do we now need to boot the liveDVD and run a file system check ? 

[INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-04
> **Bashing-om said:**
> ariel8; Umph;

As before, you could get a terminal, now you can not ??? And seems now X will not start !
What has transpired to make this turn of events ?

Do we now need to boot the liveDVD and run a file system check ? 
[INDENT]sometimes I wonder[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

i can still get the terminal, and X did not start before the only other things i installed before the graphics driver are LMMS(Linux MultiMedia Studio) and lincity-ng

---

### Post by Bashing-om on 2014-10-04
ariel8; OK ;

Post #11 at the terminal.
In the terminal execute each command in sequence - from that terminal - 
once complete
reboot and see a GUI .

[INDENT][INDENT]that is the plan
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-05
> **Bashing-om said:**
> ariel8; OK ;

Post #11 at the terminal.
In the terminal execute each command in sequence - from that terminal - 
once complete
reboot and see a GUI .[INDENT][INDENT]that is the plan
[/INDENT]
[/INDENT]

did not work, i tried to type ```
startx
``` but it still gave me the same error
EDIT: i think i found the problem, here is an error that i get when i do```
sudo apt-ger install --reinstall xserver*
```:
```
The following packages have unmet dependencies:
 xserver-xorg-input-mtrack : Conflicts: xserver-xorg-input-multitouch but 1.0~rc2+git20110312-2build is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2014-10-05
ariel8; OK !

So, hook up a regular mouse to the box and remove both packages. When the system is in a stable condition you can (re-)install ONE of them.
```

sudo apt-get remove --purge xserver-xorg-input-mtrack xserver-xorg-input-multitouch

```

see now what happens.

[INDENT][INDENT]one thing, or another
[/INDENT][/INDENT]

---

### Post by ariel8 on 2014-10-06
Solved! I re installed linux
Thanks alot om, i cant thank you enough for helping me

---

### Post by Bashing-om on 2014-10-06
ariel8; Hey !

OK ! .. The nuclear solution always works !
Please mark this thread solved; Top of post -> thread tools.

And I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

