---
title: "A lot of problems"
date: 2007-01-04
forum: General Help
---

### Post by Tunafish599 on 2007-01-04
Hye,

this is my first post here and probably the longest too :P

Last week I installed Ubuntu 6.06 Dapper Drake together with dual boot program Grub, everything worked fine, I updated the Kernel and in Grub there were now 2 kernels, the old one and the updated one..
I installed a few programs(no big ones, some like Kopete etc) and I decided to give Beryl a try.. I looked for the installations and tried the AIGXL installaltion from the beryl.wiki page..  But problems are always behind the corner and I encountered a problem with this command:

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`

giving me the error:

E: Couldn't find package linux-dri-modules-2.6.15-27-386 

So, I asked my friend(who also uses linux) what to do and he said that I could try the XGL installtion, it worked fine for him(even better the aiglx) 
I was like, yeah why not? so i ran the sudo apt-get remove xserver-xorg-air-core command and started with this guide:

[http://www.biodesign.com.ar/blog/?p=16](http://www.biodesign.com.ar/blog/?p=16)

the direct rendering answer was NO so I searched for drivers for my video card, I installed the 2 of Easyubuntu(which I installed practically everything with) and the ones found on the wiki page of Beryl itself:
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

sudo cp /ect/X11/xorg.conf /ect/X11/xorg.conf.orig;
 sudo nvidia-xconfig -composite; sudo nvidia-xconfig -allow-glx-with-composite
 sudo nvidia-xconfig -render-accel; sudo nvidia-xconfig -add-argb-glx-visuals

thoe commands

so that worked, I installed beryl and that worked too.. I was pleased, such an easy installation for such a cool program

but that was till i rebooted :(
my keyboard settings wer changed, the beryl manager booted up but that was all so i tried a lot of things, rewriting the xorg.conf file withthe xorg.conf.old file etc and at the moment the only thing i get when i boot ubuntu(in both of the kernels) is the login screen like a terminal(or dos) so not the REAL intro screen but in black and white(hope you guys understand)

I don't really know what to do now so if anyone can help me :D

I did a lot of things but isn't there a format function for linux too or something :o

Thanks

---

### Post by budgie9 on 2007-01-04
Go here for a list of commands and the format command in Linux.
[http://www.perpetualpc.net/srtd_mkfs.html](http://www.perpetualpc.net/srtd_mkfs.html)

---

### Post by Tunafish599 on 2007-01-04
yeah ok, but isn't there a way with commands so I can get into ubuntu again?

---

