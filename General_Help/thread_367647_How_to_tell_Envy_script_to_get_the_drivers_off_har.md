---
title: "How to tell Envy script to get the drivers off hard disk??"
date: 2007-02-22
forum: General Help
---

### Post by hadiriazi on 2007-02-22
Hi all,

I have a very slow dial up connection and I want to install the latest nvidia drivers via Envy script. I have already download the newest drivers from nvidia and now want to use envy to install it. The problem is that envy tries to download the drivers off the site again but I don't want it to. I want it to use the driver from hard disk. 

If it's possible at all ...
Please tell me how :(

Thanks

---

### Post by igknighted on 2007-02-22
> **hadiriazi said:**
> Hi all,

I have a very slow dial up connection and I want to install the latest nvidia drivers via Envy script. I have already download the newest drivers from nvidia and now want to use envy to install it. The problem is that envy tries to download the drivers off the site again but I don't want it to. I want it to use the driver from hard disk. 

If it's possible at all ...
Please tell me how :(

Thanks

If you already have the drivers why not just install them yourself?  Just find a how-to on the forum (do not use nvidia's instructions, there are a few differences) and its really really easy.

---

### Post by wh0rd on 2007-02-22
open the script with your favorite text editor and comment out the lines that downloads the drivers, save the script, and run it.

---

### Post by hadiriazi on 2007-02-22
> **wh0rd said:**
> open the script with your favorite text editor and comment out the lines that downloads the drivers, save the script, and run it.

Could you please show me how? and which line exactly I should change?

---

### Post by cmost on 2007-02-22
Why go to all that trouble when you can simply do what the other poster suggested...install the driver yourself, directly.  All the envy script automates is the fetching and running of the driver package and the necessary install tools.  You've already fetched it yourself, now all you have to do is run it.  It's easy.  Simply do the following:

1.  Open synaptic and ensure you've installed build essential and the kernel headers for your running kernel.  (Searh keywords:  build-essential and kernel)
2.  CTRL+ALT+BACKSPACE to kill the X server
2.  type (without quotes) "sudo sh /path/to/nvidia/driver NVIDIA-Linux-x86-1.0-9746-pkg1.run"
3.  Follow the prompts.  That's it!

I find it useful to modify my xorg.conf to change "nv" for "nvidia" in advance of killing the X Server, then, tell the nvidia installer NOT to modify your xorg.conf for you.  To do that, open a terminal and type "sudo gedit /etc/X11/xorg.conf"  Save the changes, then kill the X server.  If you do find yourself at the command line and you need to modify xorg.conf, then type "sudo nano /etc/X11/xorg.conf)  Nano is easier to use than Vi or Vim.  Remember, knowledge is power.  Good luck.

---

### Post by geezerone on 2007-02-22
Hi

Having problem with the Envy script which I accidentally installed the beta (6.1) and then purged this to install the latest stable nvidia driver (0.8.2). The beta driver did work but when I installed the stable one I was left with no X driver (just black screen where there should be a login window).

I changed the xorg.conf entry from "nv" to "nvidia" and this toggles whether I get a login window or blank screen respectively. I don't know the difference between these two btw.

Any ideas as to what is wrong and how to check which driver is installed?

---

### Post by dannyboy79 on 2007-02-22
y9uo can check which driver is installed by typing ```
dmesg | grep NVIDIA
```

this is what mine says:
[17179598.612000] nvidia: module license 'NVIDIA' taints kernel.
[17179598.876000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006

oh, the nv driver is the free open source driver for nvidia cards but I don't think this allows opengl and direct rendering so most people install the real non-free nvidia driver which you get mush better performance from. what card do you have? the newest envy script should detect your card and install the correct driver and install linux-restricted-modules etc etc for ya. did you try to run envy?

---

### Post by geezerone on 2007-02-22
I used the envy script on other machines ok but using it with this PC (nvidia 6600 gfx card) i get blank screen with NVIDIA UNIX x86 Kernel Module  1.0-9746. I used envy to accidentally install the beta driver which worked but trying the stable one doesn't. :confused:

---

