---
title: "&quot;nomodeset&quot; in GRUB makes video unresponsive and unusable"
date: 2013-08-05
forum: General Help
---

### Post by david_n_c2 on 2013-08-05
Using 13.04 I get the black screen of death unless I put "nomodeset" in GRUB. If I do this then I can boot but the video/display performance is abysmal. I only get 2 resolutions available (1024x768 & 640x480) and the speed is very poor. The aspect ratio of both resolutions is wrong for my screen at 4:3 but there is no option that gives 5:4, so everything is distorted. With the power plugged in the screen is bright. As soon as I unplug power the screen brightness drops to a level where I can barely see it. But, if I take nomodeset out of GRUB then I can't boot. Ubuntu 13.04 is not usable on my laptop as things stand. Does anyone know how to solve this? Thanks for any help.

---

### Post by grahammechanical on 2013-08-05
The nomodeset option is not meant as a permanent solution but just as means of getting us to a desktop where we can install a proprietary video driver. Linux gets the monitor settings by reading data stored in the monitor and it uses that information to set the video mode to the optimum resolution settings of the monitor provided by the manufacturer. Running Linux with nomodeset stops Linux with trying to find the optimum video mode by reading the data in the monitor. The performance is poor and the options are limited to prevent damage to the monitor.

Have you tried using Advanced Options Recovery mode>Resume. That might get you to a desktop with a better user experience. Have you tried using a different video driver? Go to System Settings>Software & Updates>Additional Drivers tab. Allow the utility a little time to search for drivers and you will see a selection that you can experiment with. And you may need to experiment. Some of the drivers are experimental themselves but they may solve issues that the older drivers do not solve.

Regards.

---

### Post by david_n_c2 on 2013-08-05
[SIZE=1][SIZE=1][SIZE=2]That's extremely helpful grahammechanical. Thanks for responding. The laptop is a Samsung NP-Q45 with a Intel GMA X3000 GeForce 8400M G graphics adaptor and the LCD panel is 12.1inch WXGA (1280x800). I have Ubuntu 13.04 installed on 2 laptops and the other one has shown no difficulties at all so I assume this is connected to hardware or possibly installed packages. otherwise the 2 installations are identical. I am not knowledgeable about Ubuntu and don't know where to find "Advanced Options>Recovery mode>Resume". Where is that? Thanks for your help.[/SIZE][/SIZE][/SIZE]

---

### Post by oldfred on 2013-08-05
Advanced options is the sub-menu of grub and recovery mode is a boot option. It now has nomodeset as a default.

You have both Intel & nVidia? If so then you may need Bumblebee.

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)


 NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)

---

### Post by VMC on 2013-08-05
david, Try using *modeset=0* instead. It should give you better resolutions.

---

### Post by stefan_bahrens on 2013-08-05
[SIZE=2][FONT=arial]VMC - would the line in grub look like this-
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset=0"

oldfred - I hadn't noticed that but yes, that's how the manual describes the video adaptor
Intel GMA X3000 GeForce 8400M G
You're right it's got 'Intel' & I recognise 'GeForce', now you mention it, as an Nvidia brand. That's a bit odd then.[/FONT][/SIZE]

---

### Post by david_n_c2 on 2013-08-05
[SIZE=2][FONT=arial]Sorry about that. I  messed up re-registering after the recent hack and ended up with 2 active accounts. You get logged in automatically now and I'd changed PCs, if you see what I mean. I am happy to delete one, if that's possible.

VMC - would the line in grub look like this-
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset=0"

 oldfred - I hadn't noticed that but yes, that's how the manual describes the video adaptor
 Intel GMA X3000 GeForce 8400M G
 You're right it's got 'Intel' & I recognise 'GeForce', now you mention it, as an Nvidia brand. That's a bit odd then.[/FONT][/SIZE]

---

### Post by david_n_c2 on 2013-08-30
I admit defeat. I've tinkered with this but was forced to give up. I decided to re-install Ubuntu 13.04 from DVD and re-format the hard disk. My reasoning here was that Ubuntu was booting and working fine on my laptop up until about one month ago and then I started getting "the black screen of death" for no reason I could see. Assuming something got broken I thought re-installing would fix the problem. Imagine my distress (frustration?) when I found I could not re-install because after selecting "Install Ubuntu" I just got the black screen back. So, I'd appreciate any advice on how to re-install Ubuntu 13.04 when the display goes to black after selecting install. Anyone come across this?

---

### Post by buzzingrobot on 2013-08-30
Can you go into BIOS setup and disable the Nvidia and try to install using the Intel?  Or, disable the Intel and boot using the Nvidia? (It will be the 'Discrete' entry.). You shouldn't need nomodeset for the Intel, but probably for the Nvidia.

---

### Post by oldfred on 2013-08-30
Some systems BIOS lets you set which video mode is used by default. Other just have software to switch it. Check BIOS for settings.

If in nVidia mode nomodeset should get you past the blackscreen, until you install the nVidia proprietary driver.

Intel is just supposed to work as it only has the one open source driver. But some version seem better supported and some do need certain boot parameters to work.

this says the X3000 is a desktop chip? But under the Linux heading it says it uses Intel drivers by Tungsten Graphics, so I do not know if then you need a parameter on the i915 to recognize that or not.
[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

Just to get in you can try the generic setting also.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by Quackers on 2013-08-30
The possible boot options (or amendments to /etc/default/grub) are nomodeset or modeset=0 NOT nomodeset=0

---

### Post by VMC on 2013-08-30
> **david_n_c2 said:**
> I admit defeat. I've tinkered with this but was forced to give up. I decided to re-install Ubuntu 13.04 from DVD and re-format the hard disk. My reasoning here was that Ubuntu was booting and working fine on my laptop up until about one month ago and then I started getting "the black screen of death" for no reason I could see. Assuming something got broken I thought re-installing would fix the problem. Imagine my distress (frustration?) when I found I could not re-install because after selecting "Install Ubuntu" I just got the black screen back. So, I'd appreciate any advice on how to re-install Ubuntu 13.04 when the display goes to black after selecting install. Anyone come across this?
I somehow missed you reply. If your getting no display when using the livecd (if I'm reading your question right), then use the 'F6' key and add "modeset=0" *modeset* is preferred over the older *nomodeset* because it gives better resolution - if it works. Try both so you know. 
note: this works for my nvidia integrated graphics. I'm unsure about intel.

---

### Post by david_n_c2 on 2013-08-31
OK very helpful. Thanks. I'll give it another go and see what I can do through the bios.

---

### Post by david_n_c2 on 2013-08-31
Quackers - I have noted your correction. Thanks.

---

### Post by david_n_c2 on 2013-09-09
I was wrong about the type of graphics adaptor my Samsung Q45 laptop has. If I do lspci (with nomodeset) I get this -

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f00fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f01fffff

So it's an embedded Intel GM965 graphics chip. This output shows that no driver is loaded. It would be mentioned in the lines starting "configuration:". I got a visible desktop rather than the black screen of death by selecting "nomodeset" when I reinstalled Ubuntu 13.04. I think it was one of the options under F6. However the performance is hopeless. I have installed the app that will load Intel graphics drivers from here -
[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)
I ran it to install Intel graphics drivers. It appeared to do something. I have no idea if these dedicated Intel drivers will load while I still have nomodeset in GRUB. I don't know how to remove nomodeset from GRUB, or even where the option appears in GRUB.
If I hold shift down while booting I get the GRUB menu. If I click 'e' I can theoretically edit GRUB but I cannot find a line in the text on screen that contains 'nomodeset'. Do I just delete the word? I really don't want to reinstall Ubuntu yet again. Thanks for any help.

---

### Post by oldfred on 2013-09-09
If you manually add nomodeset at grub menu, it is a one time edit. You have to change a grub configuration file.         /etc/default/grub to make it permanent into grub menu.

You then can try this instead of nomodeset, there is only one Intel open source driver:
      
 i915.modeset=1

---

### Post by david_n_c2 on 2013-09-11
Thanks oldfred. With the spirit of adventure I tried a couple of other things which make me wonder if this is possibly a hardware fault -
1) I tried to install an older LTS version, Ubuntu 12.04LTS. I couldn't do it. The laptop appears to be trying to boot from the dvd. I got some jumbled letters and flashing on the display, then back to black screen of death.
2) I tried to install Windows XP. I couldn't do it.  The laptop appears to be trying to boot from the Windows XP dvd. I got some jumbled letters and flashing on the display, then back to black screen of death.
3) I tried to get into the bios by holding down F2 while booting. I couldn't do it. I got some jumbled letters and flashing on the display, then back to black screen of death.
This is beyond my experience. Which bit of my laptop has failed? Has it been invaded by aliens? Thanks for any suggestions.

---

### Post by oldfred on 2013-09-11
It can be difficult to tell if software or hardware many times. If not a desktop where you can swap hardware then all you can do is experiment with different software and different settings.
But if you cannot even get into BIOS that is not a good sign.

---

### Post by david_n_c2 on 2013-09-13
Thanks oldfred. I got a computer technician to take a look. He tried swapping out the RAM which was my first thought, but this made no difference. Next he made an inspired guess and re-secured the processor with thermal paste. That worked. So it seems that it was overheating. This allowed me to be able to boot again but only with "nomodeset" in GRUB boot options. I decided to go back to Ubuntu 12.04LTS since I'd used it for a long time with no problems. This has done the trick. No more black screen of death, so the problem is solved.

---

### Post by oldfred on 2013-09-13
That is a new one for this issue. :)

But I do know that too much or too little paste and overheating can cause all sorts of issues.

---

