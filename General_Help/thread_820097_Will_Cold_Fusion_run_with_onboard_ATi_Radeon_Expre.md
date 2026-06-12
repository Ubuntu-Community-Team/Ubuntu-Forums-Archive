---
title: "Will Cold Fusion run with onboard ATi Radeon Expresss 1250?"
date: 2008-06-05
forum: General Help
---

### Post by tuxxy on 2008-06-05
Hey guys,

Planning to install Ubuntu 8.04 on a second box tomorrow, no graphics card just onboard ATi chipset which is *ATi Radeon Expresss 1250* Manual says it based on the ATi 690G/690V chips, its a fairly new system.  

I attempted to test it today by running the live feature on the CD however it wouldnt allow me to upgrade the visual settings so am wondering was this because I had not done a full install?

Also am I right in assuming that these visual display settings included in the Ubuntu install is cold fusion...

any help aprreciated! #-o

EDIT: I found the following information regarding the 3D capabilities of my chipset or so I beleive,


3D Acceleration Features

        * 3D Texture support, including projective 3D textures.
        * Complete 3D primitive support: points, lines, triangles, lists, strips and quadrilaterals and BLTs         with Z compare.
        * Anti-aliasing using multi-sampling algorithm with support for 2, 4, and 6 samples.
        * New generation rendering engine provides top 3D performance.
        * Support for OpenGL format for Indirect Vertices in Vertex Walker.
        * Full DirectX® 9.0 support (Vertex Shader version 2.0 and Pixel Shader version 2.0)
        * Support for up to 512b per pixel formats (4 color case).

This seems like it may run the software however it doesnt explain why it wouldnt work today on the live software and also no drivers were available for install...

---

### Post by tuxxy on 2008-06-06
I guess not?

---

### Post by jtrindle on 2008-06-06
I'm going to guess you're not getting any responses because of the title... "Cold Fusion" is a web application development system but I think you're after "Compiz Fusion".

I'm sorry, I don't have any useful help.

---

### Post by Forlong on 2008-06-06
> **tuxxy said:**
>   I attempted to test it today by running the live feature on the CD however it wouldnt allow me to upgrade the visual settings so am wondering was this because I had not done a full install?
You need the proprietary fglrx driver for that card.
It's not possible to use that on the Live CD because it needs a reboot to use the proper kernel module, thus it's not in the Live CD's "Driver Manager".

But you'll be able to install it just fine after the install and Compiz shouldn't be a problem either.

---

### Post by zeronothing on 2008-06-06
Yes it will work, I bought an Acer laptop with the same onboard graphics chipset. It works really well and no problems trying to get it to work. I would recommend installing Envy to install the graphics drivers. go to the [[COLOR="Blue"]website[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html") and click "EnvyNG" to install the program. This is what I did and had no problems getting the correct drivers up and running.

---

### Post by Forlong on 2008-06-06
Please do not install the driver via envy for no reason.

---

