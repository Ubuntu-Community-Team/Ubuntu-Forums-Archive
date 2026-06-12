---
title: "what about drivers ?"
date: 2013-10-18
forum: General Help
---

### Post by Bill_Charlaftis on 2013-10-18
I want to install ubuntu to **SATELLITE P50-A-118.** The problem is that I had never install linux before. For this reason I would like to ask you if I need to find a kind of drivers (like on windows) before I start the installation. If so where can find them? 
I m wating for your response.

---

### Post by Vaphell on 2013-10-18
in general you get drivers out of the box, there might be some exceptions like with proprietary driver for nvidia chipset your hardware apparently has (you get open source one by default, but it doesn't have all the features so switching to nvidia one is desirable)

[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) 
#1 is what you want as an inexperienced user

that said, give ubuntu a spin in live mode, without installing. It will be slower than the true install but you can see what you can expect, should you commit to ubuntu.

---

### Post by Bill_Charlaftis on 2013-10-18
Thanks for your response.
So your advice is to boot ubuntu via usb stick and after that to follow the instructions you sent me in that url  ,
right ?

---

### Post by Vaphell on 2013-10-18
live mode is not permanent if i remember correctly so there is no point in installing stuff as the changes won't stick, but you still have that option if you wish. What i had in mind was testing if all other devices work properly, touchpad, sound adapter, you name it.

Are you going to dual boot?

---

### Post by grahammechanical on 2013-10-18
This makes it all more complicated

> 
[LIST]
[*]NVIDIA® GeForce® GT 740M with CUDA&#8482; Technology and NVIDIA® Optimus&#8482; Technology
[/LIST]


You need a special video driver for Optimus and the Nvidia driver still under development and the Open Source driver (Bumblebee) is still under development.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

[http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html](http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html)

Another complication is whether Windows 8 is pre-installed. Ubuntu can handle Secure boot and GPT/UEFI but you need to be prepared. You will see posts on this forum giving advice to those wishing to install Ubuntu along side Windows 8.

May I suggest that when you install you do not tick the box Install Third Party software. That will activate a proprietary video driver that may not be suitable and you may not get to a working desktop. By leaving that box unticked we get the standard Open Source video driver called Nouveau. That may get you to a desktop but without much Optimus support but from there you can activate either Bumblebee or the correct Nvidia driver, which seems to be Nvidia 319 or later. But note it is starting to look that you need Ubuntu 13.10 which was released yesterday.

To install that third party software after installation, open the Ubuntu software Centre and search for Ubuntu Restricted Extras and click the Install button.

Regards.

---

### Post by Bill_Charlaftis on 2013-10-18
> **Vaphell said:**
> live mode is not permanent if i remember correctly so there is no point in installing stuff as the changes won't stick, but you still have that option if you wish. What i had in mind was testing if all other devices work properly, touchpad, sound adapter, you name it.

Are you going to dual boot?

Yes, I want to dual boot.
So you tell me to install ubuntu and after that to find  ,download and install  the linux device drivers via device manufacture site . The only exception would be nvidia , or I would face up and other issues .

---

### Post by grahammechanical on 2013-10-18
Once 13.10 is installed go to System Settings>Software and Updates and open the Additional Drivers tab. Allow it time to find the drivers. It may offer a suitable driver. Some download from the Nvidia website thinking that latest must equal greatest but often it equals experimental. We can hit problems if we do not know what we are doing.

I do not have Optimus technology but I see from Additional Drivers tab that I have Nvidia-319 (proprietary, tested) and Nvidia-319-updates (proprietary) available. You may find one of them acceptable and installing it a lot easier than installing a prorietary video driver from the command line.

Regards

---

### Post by Bill_Charlaftis on 2013-10-18
> **grahammechanical said:**
> This makes it all more complicated



You need a special video driver for Optimus and the Nvidia driver still under development and the Open Source driver (Bumblebee) is still under development.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

[http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html](http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html)

Another complication is whether Windows 8 is pre-installed. Ubuntu can handle Secure boot and GPT/UEFI but you need to be prepared. You will see posts on this forum giving advice to those wishing to install Ubuntu along side Windows 8.

May I suggest that when you install you do not tick the box Install Third Party software. That will activate a proprietary video driver that may not be suitable and you may not get to a working desktop. By leaving that box unticked we get the standard Open Source video driver called Nouveau. That may get you to a desktop but without much Optimus support but from there you can activate either Bumblebee or the correct Nvidia driver, which seems to be Nvidia 319 or later. But note it is starting to look that you need Ubuntu 13.10 which was released yesterday.

To install that third party software after installation, open the Ubuntu software Centre and search for Ubuntu Restricted Extras and click the Install button.

Regards.
To be honest I do not understand a lot about the video card.

---

### Post by Bill_Charlaftis on 2013-10-18
> **grahammechanical said:**
> Once 13.10 is installed go to System Settings>Software and Updates and open the Additional Drivers tab. Allow it time to find the drivers. It may offer a suitable driver. Some download from the Nvidia website thinking that latest must equal greatest but often it equals experimental. We can hit problems if we do not know what we are doing.

I do not have Optimus technology but I see from Additional Drivers tab that I have Nvidia-319 (proprietary, tested) and Nvidia-319-updates (proprietary) available. You may find one of them acceptable and installing it a lot easier than installing a prorietary video driver from the command line.

Regards
So I think that I understand now.

---

### Post by Bill_Charlaftis on 2013-10-18
I think that I would install ubuntu by using default drivers and I will be in touch with the manufacture sites .When they would release them I m going to update the drivers to manufacture edition.

---

