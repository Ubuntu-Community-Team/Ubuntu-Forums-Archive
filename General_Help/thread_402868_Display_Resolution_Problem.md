---
title: "Display Resolution Problem"
date: 2007-04-06
forum: General Help
---

### Post by jacobraj on 2007-04-06
I am new to linux and I installed ubuntu on my laptop (Samsung v25), The only resolution option i get is 640*480 with 60HZ refresh rate, I wanted to change the resolution, but i don't know how to proceed, Can anyone guide me plz?

Thanks
Jacob

---

### Post by Shay Stephens on 2007-04-06
**Changing Resolution**
If the computer does not give you the option of choosing the highest resolution for your monitor, do this:

```
lspci
```

That gives a list of the devices installed into the pci bus. Your video card should be among them. Just note which one it is so you can select it in the next step.

again in the terminal

```
sudo dpkg-reconfigure -phigh xserver-xorg
```	

That will ask you to choose the graphics card manufacturer. I have an nvidia card, so I selected the "nv" entry. Then it asks you to choose the resolutions the card can support. Use the cursor keys to highlight resolution and hit the space bar to check it. I have an lcd monitor, so I just selected the native resolution (1280x1024). When you are done, restart the session by doing a ctrl+alt+backspace or just reboot.

---

### Post by jacobraj on 2007-04-06
Thanks very much for your response, 

I did exactly as you mentoined before and rebooted the system, now i could get the xserver running,It says,

Fatal Server error

Caught Singal 11 Server aborting.

X10:fatal 10 error 104 (Connection reset by peer) on X server ";0.0" after 0 requests with 0 events remaining.

-Steps i did:

lspci:

VGA: Intel Corporation 82845G/GL[Brookdate-G]/GE Chipstet Integrated Graphics Device (rev0)

mine is a integrated graphics card, so i selected the VGA option and the selected the resolution and rebooted.

Now the Xserver is not running.

Any help really apprecaited

Thanks

Jacob

---

### Post by Shay Stephens on 2007-04-06
It is an intel card, so there should have been a selection for that.  What you will likely have to do is edit the xorg.conf file and change the video driver back to vesa.  To do that, log in, run

```
sudo nano /etc/X11/xorg.conf
```

Find the video driver entry and change it to say vesa.  I have an nvidia card so my section looks like this:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```

I would change the "nvidia" to "vesa", your's probably says "VGA", so change it to "vesa"


Press control X and save the file, then reboot.  That should get you back into the x server, then you can try it again hehehe.

---

### Post by Shay Stephens on 2007-04-06
It looks like the driver for the intel card might be the i810, but I am not 100% sure of that.

---

### Post by censored77 on 2007-04-06
I have a nvidia card. Driver seems to have installed ok, but can still only access 640 x 480. I've followed your proceedure on this thread, and various resolutions were already selected. Still when I go to change the resolution, the only option is 640 x 480. Any ideas?

---

### Post by Shay Stephens on 2007-04-06
Do you have the nvidia driver?  Check synaptic for nvidia-glx

---

### Post by censored77 on 2007-04-06
Yes, and I get the nvidia splash screen just before login. So it does appear to be working ok...

---

### Post by jacobraj on 2007-04-09
Hey guys,

Thanks very much for yoor help,

Resolution worked ok as expected

Jacob

---

