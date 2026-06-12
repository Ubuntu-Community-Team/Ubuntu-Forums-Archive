---
title: "Weird picture on screen"
date: 2006-10-26
forum: General Help
---

### Post by narvik86 on 2006-10-26
Hi. I just installed Kubuntu 6.10. I had a problem with installation, and i have big problem now. I have so weird view. It happens after Kubuntu Logo, when progress bar ends.(i mean its loaded) I think it's something with resolution maybe. I had the same picture when i tried to install kubuntu. But before launching livecd i changed (by F4) resolution to 1024x768 32bit and it helped, but i didn't have mouse cursor. Have you got and ideas how to fix it? Thanks. 
My pc:
AMD Sempron 1,5GHz
1280MB RAM
ECS KT600A
GeForce 6800GS BLISS 512MB 256bit
hdd WDigital 120GB
Sorry for my english.
Here is the strange pic:
[[IMG]http://images4.fotosik.pl/183/b37124c363ccfed0m.jpg[/IMG]](http://www.fotosik.pl/showFullSize.php?id=b37124c363ccfed0)

---

### Post by krodos on 2006-10-27
I'm having the same problem.  I was using the AMD64 version.  Also my progress bar is in black and white.  To get past the screen you need to Ctrl + Alt + F1, once in there login.  What I did then was type (ignore the ""):
"/etc/init.d/gdm stop".  
Next type: 
"sudo dpkg-reconfigure xserver-xorg".  
Run though that setup set your video card to vesa, continue keeping same options then, for resolutions set 1024x768, then set depth to 16, then finish up by clicking default answers.  This should set the video card to be a basic video card which should load Ubuntu.  
Now type: 
"/etc/init.d/gdm start". 
This should load Ubuntu up, it will look really crummy.  From there you should be able to install the video drivers.  Post back if you need more help.

---

### Post by narvik86 on 2006-10-29
I solved this problem before reading your post :) But thank you! I've installed graphic driver with guide, i picked up method I offline installation. I downloaded the package and installed with guide. It works for me. Here is link to the guide:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOWTO:_Latest_NVIDIA_drivers](http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOWTO:_Latest_NVIDIA_drivers)

---

