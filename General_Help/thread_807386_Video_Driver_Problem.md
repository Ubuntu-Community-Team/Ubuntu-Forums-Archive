---
title: "Video Driver Problem?"
date: 2008-05-25
forum: General Help
---

### Post by spark29 on 2008-05-25
Since I've installed Ubuntu on this computer (this is my first linux experience) I've had a problem where at random times colors just fill the screen and the computer crashes. The cpu fan doesn't stop spinning or anything but I can't use control alt backspace either. However, recently, I've been trying to get Warcraft 3 to run in cedega and wine and neither have worked. It was recommended that I update my video drivers. I believe I have the latest drivers for my s3 unichrome pro integrated graphics chip, as I've checked in the synaptic download manager. So I figured I could try the default drivers, the vesa drivers. However, when I try to edit the xorg config file, my driver settings (i think this is video) look like this

Section "Device"
	Identifier	"Configured Video Device"
EndSection

And from the examples I have seen in how to change drivers none have this type of format.

I am really interested in getting my computer to quit random crashing and I hope this fixes my wine / cedega video issues.

---

### Post by EXCiD3 on 2008-05-25
S3 unichrome pro has absolutely awful linux support for now unfortunately. There are a couple different drivers but here is the wiki page for the UniChrome support in ubuntu: [https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by spark29 on 2008-05-26
There is no specific driver for my chipset, the k8m800. Couldn't I just use the generic vesa drivers? I tried adding a line in for Driver  "vesa" into the file with the format mentioned above, but the gui failed and I had to reboot. Any advice?

---

### Post by spark29 on 2008-05-26
Also, I tried using one of the drivers and the installer quit with the message 

"This driver package is only support the default kernel
  "2.6.20-15-generic" for Ubuntu 7.04"

So...

---

### Post by EXCiD3 on 2008-05-26
You can use the vesa drivers for it, but you wont get a very good resolution i dont think. Try running "sudo dpkg-reconfigur xserver-xorg" in terminal to reconfigure your xorg which should set it to the vesa drivers.

---

### Post by spark29 on 2008-05-26
I ran that command from the terminal, and the only video option I was met with was using the "kernel framebuffer device interface", nothing about using vesa drivers. Most of the questions involved keyboard stuff, not graphics. I'm stuck. After saying yes to the kernel framebuffer dialog, my config file looks like this

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Instead of the above post. Any suggestions?

---

### Post by EXCiD3 on 2008-05-27
Typically when someone has graphics problems a simple run of that command will reset the drivers back to vesa. For some reason the Driver section still isnt showing up on your xorg. You can try adding this to the section and restarting the xserver to see if it does anything: ```
Driver     "vesa"
```

---

