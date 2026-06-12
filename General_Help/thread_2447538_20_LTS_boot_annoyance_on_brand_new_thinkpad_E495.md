---
title: "20 LTS boot annoyance on brand new thinkpad E495"
date: 2020-07-21
forum: General Help
---

### Post by KayaE on 2020-07-21
Hello,

i installed Ubuntu 20 lts on a brand new Thinkpad, all seems fine but having boot problems sometime.
i searched boot annoyance tags in the forum.
issue i am havin looks similar like this [https://ubuntuforums.org/showthread.php?t=2440701](https://ubuntuforums.org/showthread.php?t=2440701)
[COLOR=#000000]"On roughly 3/4 attempts [/COLOR][COLOR=#000000]system regularly fails to boot. The Lenovo logo appears when I power on the laptop, then it   disappears.."  
boot seems stuck on a blank screen (mouse cursor showing up but it can not move)
[/COLOR][COLOR=#000000]I press and hold the  power button [/COLOR][COLOR=#000000]to power off and pass the stuck boot situation. Restarts are working fine in general, login screen shows without a problem.
[/COLOR]
My system is: 
Lenovo ThinkPad E495 AMD Ryzen 7 3700U 8GB 512gb SSD
Radeon Vega Mobile Gfx
No dual boot, Latest updates are installed.


Can you guide me to try something to fix this?

---

### Post by mastablasta on 2020-07-21
try with iommu=soft kernel parameter; see [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

i had similar issue on ryzen5: [https://ubuntuforums.org/showthread.php?t=2446942](https://ubuntuforums.org/showthread.php?t=2446942)

if it works make sure you test all peripherals (USB ports etc) before changing boot option permanently.

also i posted a bug. if work arround works, try a test kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1887218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1887218)

i already installed plenty of stuff so i would hate for install to break.

---

### Post by KayaE on 2020-07-21
Thank you **mastablasta. **i will try to understand your instructions and type my experience back here.
[TABLE="class: table table-hover table-striped searchResultsTable"]
[TR]
[TD="class: tr ts"] 
[/TD]
[TD="class: en tm"][/TD]
[/TR]
[/TABLE]

					[ ]("https://ubuntuforums.org/member.php?u=964486")[URL="https://ubuntuforums.org/member.php?u=964486"][B][COLOR=#DD4814][B]
[/B][/COLOR][/B][/URL]

---

### Post by mastablasta on 2020-07-21
temporary setting boot options is easy. press shift (or Esc) on start to get to GRUB, press e and enter the boot parameter (iommu=soft) just after quiet splash. then crtl+x to boot. if all is good then you can make it permanent (for now).

another options is adding kernel posted on launch pad. if that works, then you could confirm and they will add it to normal kernel in LTS so that everyone's (well at least those with AMD) boot gets fixed.

---

### Post by KayaE on 2020-07-21
i went in to grub. (to help other readers: on Lenovo e495,  first tab esc brings device specs screen and second tab on esc opens grub menu.)
i added parameter (iommu=soft) just after quiet splash. so, it looked like this:  quiet splash iommu=soft
i checked wifi and bluetooth connectivity, USB ports, multimedia. They all worked fine.

i just want to be sure before making this update permanent.
my question is did i type the parameter in the right place? 
Because on your ryzen 5 not booting topic here [https://ubuntuforums.org/showthread.php?t=2446942](https://ubuntuforums.org/showthread.php?t=2446942)
i saw the code GRUB_CMDLINE_LINUX_DEFAULT="iommu=soft quiet splash"  here parameter placed **before**
but typed it **after** : quiet splash iommu=soft

so, i could not be sure if parameter i typed took effect.
position before or after quiet splash matters?
or does it change while go temporary or permanent?

---

### Post by oldfred on 2020-07-21
I do not think order of boot parameters in grub makes any difference.
I typically like to remove quiet splash, just to see boot process. I then know it is working and if error it may show. And now change to using "noplymouth" in place of quiet splash. 

Changing parameter when booting is just for that boot. Good for testing if parameter works.

To permanent change parameter you have to edit grub's configure file & update-grub.

sudo nano /etc/default/grub
# after edits
sudo update-grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)
GRUB_CMD_LINUX
    * Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMD_LINUX_DEFAULT="quiet splash"
* This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by KayaE on 2020-07-21
i edited the grub line like this "quiet splash iommu=soft" and saved it.
after 5 boots all seems ok. i will write my experience later. after more boots and checking peripherals.
thank you mastablasta and oldfred.

(possible help for other readers: i saw a warning on terminal screen while editing on gedit. 
Tepl-WARNING **: 21:13:18.135: GVfs metadata is not supported. Fallback to TeplMetadataManager. ...it goes on.
i tried (gedit admin:///etc/default/grub &) command. it comes a warning again
** (gedit:3352): WARNING **: 23:31:18.983: Loading metadata failed: The specified location is not mounted
finally i could save my grub editing on nano editor by cont+O and press enter.)

---

### Post by mastablasta on 2020-07-22
Awesome! Yes, it works well for most, only some reported issues.

can you load new kernel i linked to (last post from dev) to see if it works? : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1887218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1887218)

you can use Ukuu (for graphical loading of new kernel) or terminal.: [https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)

i mean since you can still easily reinstall if something goes too wrong (it shouldn't).

---

### Post by KayaE on 2020-07-22
after today's experience yes all seems well. grub edit worked for my boot issue.

i remember that you mentioned on your first message about loading new kernel to where you linked.
is it uploading my kernel? or downloading another kernel? will i help developers about fixing a bug? 
my computing abilities seemed low to understand linked pages above.
if i understand what and how should i do, i will try.

---

### Post by mastablasta on 2020-07-23
Ok. i understand. Well if you think you can do it, then you can try. if not, it's also good. At least we solved your issue. :)

yes, if the patched kernel worked, the patch would then make it into main Ubuntu where it would fix this same issue for everyone. if this was my own laptop i would try and do it myself.

i hope that in November new kernel from 20.10 will be loaded.

---

### Post by KayaE on 2020-07-23
i want to support new kernel and help other users.
but as i mentioned, i cant understand what should i do.
upload my kernel? or download another kernel? 
wish you could use this laptop and do it by yourself.
by the way, i can report that patch is still working. i have no boot issue after many restarts.
thank you again.

---

