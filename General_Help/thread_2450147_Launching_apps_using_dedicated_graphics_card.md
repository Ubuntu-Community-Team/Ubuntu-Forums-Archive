---
title: "Launching apps using dedicated graphics card"
date: 2020-09-08
forum: General Help
---

### Post by mcsheffrey on 2020-09-08
Don't see any option in gnome tweaks that will allow me to change the default to "Launch using dedicated graphics card" as default. How can this be set.

---

### Post by Autodave on 2020-09-08
Can you give us some info on your system please?  What version of 'buntu are you running?

---

### Post by mcsheffrey on 2020-09-08
I'm running a **[Dell G7 15.6", I7 8750H, Nvidia GTX 1050 Ti, 16GB, 256GB+1TB, 120Hz Screen]("https://rover.ebay.com/rover/0/e11051.m43.l1123/7?euid=09bfdddf5a894cdd89ddb90e905aedad&bu=43212451498&segname=11051&crd=20200824102411&osub=-1~1&ch=osgood&loc=https%3A%2F%2Fwww.ebay.ca%2Fulk%2Fitm%2F224083212733&sojTags=bu=bu,ch=ch,segname=segname,crd=crd,url=loc,osub=osub") with ubuntu 20.04**

---

### Post by CelticWarrior on 2020-09-08
On-demand hybrid graphics profile changing isn't (yet) available for Linux distros.
This means you need to use Nvidia X Server Settings to toggle profiles (and possibly reboot to apply). There's no per app configuration possible.

---

### Post by Yellow Pasque on 2020-09-09
Here is a procedure I gave to a couple people recently that seems to have worked. Your GPU is supported by 450, so no worry there.

You will need Ubuntu >= 20.04 and Nvidia driver >= 450.xx to use on-demand smoothly.
(NOTE: Make sure your GPU is supported by 450.xx driver BEFORE doing this:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/450.66/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/450.66/README/supportedchips.html) )

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-450 nvidia-prime
```
(Reboot)

Now use the following commands to save typing in the future:
```
echo "alias prime-run=__NV_PRIME_RENDER_OFFLOAD=1 __VK_LAYER_NV_optimus=NVIDIA_only __GLX_VENDOR_LIBRARY_NAME=nvidia" >> ~/.bashrc
source ~/.bashrc
```

and try changing to "on-demand" mode. (I'm not sure, but this may require another reboot or log out):
```
sudo prime-select on-demand
```

Verification (first command should show Intel/AMD and second command Nvidia):
```
glxinfo -B
prime-run glxinfo -B
```

If all goes well, you can run programs on the Nvidia GPU by prefixing the command with "prime-run" as in the glxinfo example above.

---

### Post by mcsheffrey on 2020-09-09
Thanks for the feedback, will try experimenting with some of these ideas.

---

### Post by harrisathena on 2020-09-30
what about other operating systems? Is the solution still the same?
[[COLOR=#e6e6fa][SIZE=1][SUP][SUB]friv 2020[/SUB][/SUP][/SIZE][/COLOR]]("https://friv2020.io")

---

