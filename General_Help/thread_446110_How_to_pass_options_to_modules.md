---
title: "How to pass options to modules?"
date: 2007-05-16
forum: General Help
---

### Post by rocketman768 on 2007-05-16
Hi. When I boot up, dmesg tells me:

agpgart: Unsupported NVIDIA chipset (device id: 02a5), you might want to try agp_try_unsupported=1.

How do I pass this option to agpgart? Thank you!

---

### Post by Rui Pais on 2007-05-16
> **rocketman768 said:**
> Hi. When I boot up, dmesg tells me:

agpgart: Unsupported NVIDIA chipset (device id: 02a5), you might want to try agp_try_unsupported=1.

How do I pass this option to agpgart? Thank you!

Hi,
in that case (NVidia) you pass that option through /etc/X11xorg.conf file.  
Edit adding:
> 	#Option "NvAGP" 	"0" #| disabled
	Option 	"NvAGP" "1"  #| use NVIDIA's internal AGP support, if possible
	#Option "NvAGP" "2"  #| use AGPGART, if possible
	#Option  "NvAGP" "3" #| use any agp support (Default)

to 
```
Section "Screen"
``` of that file.

good luck.

---

