---
title: "Ubuntu crashes again and again..."
date: 2006-11-27
forum: General Help
---

### Post by saygin on 2006-11-27
Hi,
I have decided to start using linux and learning it a fex weeks ago and I downloaded Ubuntu 6.10 Edgy. First, to get used to it, I booted it with live CD. While booting with the CD, sometimes (in fact always) ubuntu got crashed. Eventhough my cursor animation was frozen, I could move it, but I couldn't click on anywhere. At the same time the screen was frozen too. If I was opening a web page and the status bar was showing how much loaded, it stoped animating too. But, if I am listening to music while it happens, the music continues to play but the visuals freezes. I though it was because I was booting from CD, but after i installed ubuntu on my PC, it didn't solve the problem.It still has the same problem and I didn't understand why. I tought it was because of firefox, and reinstalled it, but it didn't affect. I said maybe it is flash player, but I could watch youtube videos. I formated the partition which ubuntu was in, and installed it again, it is still the same as it was. By the way, this time, I can see NTFS partitions. (I couldn't see it when i installed ubuntu first time). Please share your ideas, what may be the problem? I don't want to uninstall it because if I do it, I will never try to install it again! Please help.
My comp:
Pentium 4  2.8 Ghz
512 MB DDR-RAM
128 MB Nvidia Geforce 4 MX 4000 graphic card
Asus P4U800-X Mainboard
(I have 1GB swap partition)

---

### Post by rfruth on 2006-11-27
Sounds like a hardware incompatibility problem or at least a hardware problem, did / does the other OS (Win XP, NT?) run okay :-k

---

### Post by saygin on 2006-11-27
win XP runs okay. I can't guess why ubuntu is like that... ](*,)

---

### Post by shin on 2006-11-27
Maybe it is drivers related problem. Try changing your /etc/X11/xorg.conf file.

Find there your graphic card (in Section "Device") and change Driver "something here" to Driver "vesa" (it's should work, very basic driver without 3d support)
.
Then reboot X server and check if it will hung up again. If not - search google for your card and linux support. Maybe you just need to update or download another drivers for it.

---

### Post by saygin on 2006-11-27
ok, if i can change it before the crash, i will inform you. thanx

---

### Post by wieman01 on 2006-11-27
If that does not do the job, perhaps try "Ubuntu Dapper" instead. May be an option for you.

---

### Post by saygin on 2006-11-27
I am on ubuntu now, and it haven't crashed yet :) however, with this driver, my screen resolution is 1280x1024, and i want to change it because my screen refresh rate is 61 which makes my eyes hurt. When i change it to another resolution and press enter, it does not apply the change and goes back to login screen. Besides, even scrolling down the web pages are so slow. I think it is not a "good" solution for me. What do you think?

---

### Post by shin on 2006-11-27
It's not a solution at all ;) But right now you may assume that it was the driver or settings of your card. 

As this card seems to be fully supported in linux (as nvidia page says). What was the Driver value before in xorg.conf? It should be "nvidia" and make sure if you got nvidia drivers installed. For further instructions on this

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by saygin on 2006-11-28
It was written "vesa" and I changed it to "nv" as you said. I am going to intall Nvidia driver as the link you give shows. I will let you know what is changed.

---

### Post by saygin on 2006-11-28
Yes, I think it is finally solved! I installed Nvidia driver and checked whether in xorg.conf under devices, it is written "nvidia" and the problem is solved I think. Thanks a lot! You saved my linux!

By the way, I want to ask something, where can I learn which driver version I am using and If there is a newer driver, how can I install it. (Because this driver came with ubuntu but I will have to download the new ones so can you tell it how?)  I downloaded NVIDIA-Linux-x86-1.0-9629-pkg1.run and I don't know how to install. It may be even better! Thank you!

---

