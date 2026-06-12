---
title: "MCP67M and Hardy...i don't want to go back to vista..."
date: 2008-05-02
forum: General Help
---

### Post by residualbit on 2008-05-02
First of all this chipset is terrible with any operating system. I used to use only ubuntu on my old laptop, but it died and i had to get a new one. Unfortunately it wouldnt work with ubuntu 7.04 or 7.10 very well so i have been grtting my teeth with vista hoping hardy would solve all my woes. not the case.

HP dv6636nr
AMD Turion64x2 1.8ghz
4gb RAM
MCP67M chipset
NVIDIA GeForce GO 7150m

I am installing 64bit hardy, what do i need to do to get the graphics card and wireless working?

---

### Post by yaknowwat on 2008-05-02
It should hopefully work right out of the box.

If wireless doesn't work then you'll probably need to use gtkwrapper or what ever it was called.

Graphics card will activate the properiary drivers if 3d acceleration is needed so opening an OpenGL 3D game (like neverball available in synaptic) should cause a request to enable restricted drivers.

Possibly though you can enable them easily with System > Administration > Hardware Drivers

---

### Post by residualbit on 2008-05-02
neither work out of the box...only 800x600 resolution and it doesnt really detect any hardware but most importantly, the wireless card isn't recognized at all.

---

### Post by MattBD on 2008-05-02
For the wireless, your best bet is probably to use ndiswrapper. You can find this on your Hardy CD-ROM. There's two packages there, and you need to install both - Synaptic or Adept can do that for you,just make sure it's set up to be able to install from the CD. If you're new to Linux, you also might want to use the ndisgtk frontend to make it a bit easier, but this would need to be downloaded - if you can connect via Ethernet instead to install these packages, that would be a good idea.

As for the graphics card, [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") is probably your best bet - I can't say as I've never had to use an Nvidia graphics card.

---

### Post by wheels. on 2008-05-02
> **nkirk1 said:**
> First of all this chipset is terrible with any operating system. I used to use only ubuntu on my old laptop, but it died and i had to get a new one. Unfortunately it wouldnt work with ubuntu 7.04 or 7.10 very well so i have been grtting my teeth with vista hoping hardy would solve all my woes. not the case.

HP dv6636nr
AMD Turion64x2 1.8ghz
4gb RAM
MCP67M chipset
NVIDIA GeForce GO 7150m

I am installing 64bit hardy, what do i need to do to get the graphics card and wireless working?
I have pretty much the same laptop only 2gb ram so I run 32bit, It is an awful chipset I have had problems as well, I am assuming you have the broadcom 43 something or other ( I have 4312) the b43 driver will not work (for me anyway), you have to use ndiswrapper, there is a bug in hardy that prevents it from loading in the right order, [Here Is a post that I used To get it to work]("http://ubuntuforums.org/showthread.php?t=761325&page=2") as for the nvidia driver just use the hardware drivers manager System>Administration> Hardware Drivers, check enable and it should download and configure. It worked fine for me and I am running at my resolution of 1440x900 by default after installing the driver. I just wiped vista last night and the only problem I have now is overheating, keep an eye on it ( I haven't found a fix yet)
Good Luck!

---

