---
title: "1920x1080 display resolution support?"
date: 2022-10-27
forum: General Help
---

### Post by jakemaverick911 on 2022-10-27
Hi

I'm using latest Xubuntu version but can't seem to switch to 1920x1080 resolution. I'm stuck at 1024x768. I've followed the instructions on several of the online guides, just nothing works. ARandR doesn't help either. I've managed to get the 1920x1080 option in the Display's manager....but selecting that doesn't actually change the resolution, although it says it has.

I'm wondering if it's something peculiar to Xubuntu? All the guides seems to be written for Ubuntu. Xubuntu is fully updated.

Hope somebody can help....

---

### Post by MAFoElffen on 2022-10-27
Have you checked out the first three posts of my [Graphics Resolution Sticky]("https://ubuntuforums.org/showthread.php?t=1743535")? It is still relevant for 22.04 LTS, and it specific to the Linux Graphics Layer, not just a specific Window Manager.

Specifically, ensuring that you do
```

xrandr -q

```
To ensure that 1920x1080 is listed...

Then, after confirming (above), editing /etc/default/grub, changing these two lines:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash video=fbvesa:mode_option=1920x1080-32,mtrr=3,scroll=ywrap"

GRUB_GFXMODE=1920x1080x32

```

Then after saving it
```

sudo update-grub

```
Then reboot. After reboot, check to see if that mode is listed in the display settings.

---

### Post by jakemaverick911 on 2022-10-27
No, I haven't seen that, but a lot of pages to scroll through!

I have managed to add 1920x1080 in but it looks a bit odd...on the list I have 1920x1080_60.00 59.96

60Hz is my refresh rate, but it just looks odd on the list of resolutions as...well easier to paste it in!

 1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1920x1080_60.00  59.96

something may have gone alil bit wrong when i followed the Ubuntu instructions?

---

### Post by MAFoElffen on 2022-10-27
That would be the instructions for Debian Branch, RHEL, SUSE, Arch, Oracle, etc, with a few modifications to the commands. The Linux Graphics Layer, basically work the same, no matter what the other specifics are on how to apply it.

Ubuntu, and all flavors of, work the same, in the way of the "Linux Graphics Layer."

---

### Post by jakemaverick911 on 2022-10-27
ah, forgive me but it has been along time since i needed to do this...not long had all my equipment stolen so new machines now and I've not had to work with terminal commands for many years. + recently suffered some brain damage...

I can't understand why the other instructions did not work then...

But if you see nothing wrong with what i pasted above....i think all i need to do is run your commands but replace '1920x1080-32' with '1920x1080_60.00'... I just to be absolutely sure as i really don't want to brick this machine....!

---

### Post by jakemaverick911 on 2022-10-27
ah, after the reboot i've lost 1920x180 as an option :-( i need to get it back :-(

---

### Post by jakemaverick911 on 2022-10-27
these are the instructions i followed originally, should have worked right?


[https://askubuntu.com/questions/1075157/unable-to-set-my-screen-resolution-higher](https://askubuntu.com/questions/1075157/unable-to-set-my-screen-resolution-higher)

but on this distro i also have some weird looking green battery thing top right corner called presentation mode....and two icons for my wifi connection! i was going to wait until got screen res sorted before tinkering too much, but i'm wondering now....corrupted installation?

---

### Post by MAFoElffen on 2022-10-27
The commands I posted were in the format of for the video Linux kernel boot paramter... for a grub framebuffer video driver. "-32" was the color depth part of that Linux kernel boot KMS parameter... Redo them just as I posted them please. 

You tried to combine the instructions for xrandr (after the Xinit of XServer) with the for KMS modesetting of the kernel from Grub, that give the Linux Kernel a mode to boot in and gives a KMS mode (helper) for the Linux Graphics layer to start as... As you can see, combining those techniques does not work.  Those instruction do not cross over as the same. LOL

'xrandr' modesetting only works for Xorg X11 (not for Wayland) and ***is not persistent***. Which means you would have to re-enter the same each time, after the Desktop starts. To do that with 'xranr', you would have to add that to a script (such as ~/.bashrc, or custom called from startup progs)... The way I described is the accepted way for a persistent change of adding a single mode.

If you want to add more that one resolution mode, then the preferred method is via the xorg.conf file. Scripting adding modes via 'xranr' is usually reserved for a last option kind of affair, because the Layer is already up, and most of the time not initialized in a usable state... The preferred methods attempt to bring the layers of the graphics layer up in a usable state for the User... Does that make sense to you or should I explain that differently?

---

### Post by jakemaverick911 on 2022-10-28
ah, thank you! really, only understood about 10% of that, not a  programmer at all....but yep i will follow your original instructions at  some point....I just need to get to a point where i can risk bricking  this machine, sort some files out etc...but thank you again! i'll post  back here when it proves successful....!


actually, just looking again quickly...I have lost the 1920x1080 option...what's the easiest way to add that back in?

---

### Post by Shibblet on 2022-10-28
Are you in a VirtualBox?

---

### Post by jakemaverick911 on 2022-10-29
> **Shibblet said:**
> Are you in a VirtualBox?

no, but i am connected via a KVM switch....may that stop it from detecting automatically?

---

### Post by MAFoElffen on 2022-10-29
Yes. Being connected to a KVM Switch does prevent the Graphics Card or GPU from "seeing" what it is connected to (the display) and what capabilities it has.

YOu "are" on the right path...

---

### Post by Shibblet on 2022-10-31
> **MAFoElffen said:**
> Yes. Being connected to a KVM Switch does prevent the Graphics Card or GPU from "seeing" what it is connected to (the display) and what capabilities it has.

YOu "are" on the right path...

Sometimes the best solution is to stop someone from spinning, and point them toward the donkey.  ;-)

I have had multiple issues with screen resolution detection in VM's.  VirtualBox, VMWare and KVM all seemed to do the same thing.

---

### Post by MAFoElffen on 2022-11-01
> **Shibblet said:**
> I have had multiple issues with screen resolution detection in VM's.  VirtualBox, VMWare and KVM all seemed to do the same thing.
Yes. For VM's you add another few other factors to that...

- Does the video selected for the Guest support graphics acceleration. (Example: VirtGL or vGPU passthrough)
- Which resolution do you want it to be. Or do you want multiple resolutions available for it. (Easiest for that is to create an xorg.conf file)
- Graphics Scaling
- Which vHost System you are using. Each has their own ways of doing things.

I prefer KVM, though I am a DEV Tester for VMware vSphere.

---

