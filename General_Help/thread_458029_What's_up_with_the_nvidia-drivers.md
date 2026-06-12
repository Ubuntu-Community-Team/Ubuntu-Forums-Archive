---
title: "What's up with the nvidia-drivers?"
date: 2007-05-29
forum: General Help
---

### Post by loathsome on 2007-05-29
Hi there,

I'm throwing out mr. Vista on my desktop, and Feisty goes in. I'm a bit stuck now though, what drivers should I grab for my NVIDIA GeForce 7900 GT card? The «restricted drivers manager» thingy wants to download 'nvidia-glx' or something, but what about 'nvidia-glx-new'? Which one? Or should I get [these drivers from nvidia.com?](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

Appreciate your answers! (:

---

### Post by matigol on 2007-05-29
I think that nvidia-glx new is for latest-version of nvidia-cards and nvidia-glx for oldest version.
For example, i have one geforce 4 mx 440 and i must use nvidia-glx, because if i don't use it, my pc doesn't boot... and x is not charged...

With your card, i think that you can use nvidia-glx-new...

I am not a specialist yet..

---

### Post by loathsome on 2007-05-29
Thanks, I'll try out a bunch of stuff later.

:)

---

### Post by MontanaMax on 2007-05-29
I highly recommend installing Envy instead - it will determing the kernel and hardware you have installed, download, patch, and install the correct drivers for you - all in about two button clicks. amazingly fast and simple. I had always done a manual install up till this weekend, but after using Envy once I'm converted!

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck!

---

### Post by ikonia on 2007-05-29
I highly recommend against using envy and any other 3rd party products that change the way ubuntu installs software.

---

### Post by Kuoi on 2007-05-29
> **ikonia said:**
> I highly recommend against using envy and any other 3rd party products that change the way ubuntu installs software.

I second that ... but ... for Envy I make an exception.
This prog made my installation of the right Nvidia driver easy , but only after I've tried everything else , but didn't work.
After using Envy , it was installed correctly.

I shouldn't recommend any other 3rd party products that change the way ubuntu installs software either , ...  but I needed Envy 1 day .
A tip if you use Envy :
First uninstall the driver using Envy , and than Install the right driver using Envy .

Kuoi

---

### Post by loathsome on 2007-05-29
> **MontanaMax said:**
> I highly recommend installing Envy instead - it will determing the kernel and hardware you have installed, download, patch, and install the correct drivers for you - all in about two button clicks. amazingly fast and simple. I had always done a manual install up till this weekend, but after using Envy once I'm converted!

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck!
Hi, thanks - but no. I just went like ```
apt-get install nvidia-glx-new
```, went for a reboot and ta-da! Up and running. I manually had to put in my resolution in the xorg-file, though, but that took me like 15 seconds. :) Thanks for your replies, guys or girls!

loathsome :KS

---

### Post by stchman on 2007-05-29
> **loathsome said:**
> Hi there,

I'm throwing out mr. Vista on my desktop, and Feisty goes in. I'm a bit stuck now though, what drivers should I grab for my NVIDIA GeForce 7900 GT card? The «restricted drivers manager» thingy wants to download 'nvidia-glx' or something, but what about 'nvidia-glx-new'? Which one? Or should I get [these drivers from nvidia.com?](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

Appreciate your answers! (:

Just let the restricted drivers manager enable your card.  I have a 7600GT and it worked just fine.

---

### Post by fragos on 2007-05-29
IMHO, chosing an nvidia-glx package was the wisest solution.  There is a diversity of opinion on this issue with the opinion formed by what a particular user did that worked.  The safest solution is always one from the Ubuntu repositories.  Updates and upgrades will be much more trouble free if you do that.

---

