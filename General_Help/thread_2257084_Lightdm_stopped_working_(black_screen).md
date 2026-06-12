---
title: "Lightdm stopped working (black screen)"
date: 2014-12-16
forum: General Help
---

### Post by tobbe.bia on 2014-12-16
Hi
I need help with getting lightdm working again.

**Necessary background facts:**
I have a laptop with dual-boot between Windows and Ubuntu 14.04. The laptop uses the NVIDIA Optimus technology, which means that it has an integrated Intel graphics card and a discrete NVIDIA GTX card. To be able to select when I want to use the NVIDIA card and when to use the Intel card I have previously installed bumblebee ([http://bumblebee-project.org](http://bumblebee-project.org)).

**What happened:**
Today I wanted to see how well Minecraft (a game) could run on Ubuntu so I installed it and ran it. When using the NVIDIA card, I got really low FPS (even lower than the integrated Intel card) and therefore I decided to try and install nvidia-prime, which is another program like bumblebee (for handling Optimus technology). It went well but the performance was almost exactly the same as with bumblebee. I tried installing another NVIDIA driver (nvidia-46) but the performance was still the same. So I gave up on the idea of trying to get the NVIDIA card to perform better than the integrated card (which it should). I read on some forums that others were having the same issues but noone seemed to have a solution. So therefore since it didn't matter, I decided to go back to bumblebee because it has a better way of switching between graphics devices IMO. 

**The problem:**
When I went back bumblebee and then rebooted the computer the screen went black just after the Ubuntu loading symbol. So instead of a login screen it was just black. I tried some things like making sure the bumblebee configuration was correct (/etc/bumblebee) and I also tried nvidia-xconfig because I thought it was a problem with Xorg. I found a suggestion on a forum to a similar problem to install GDM and set it as the default display manager instead of lightdm. I installed it and to my amazement it now works every time I boot (using GDM login manager). I tried switching back to lightdm after apt-get purge lightdm and then reinstalling it again but it still gives me a black screen. I found this article [http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html](http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html) which seems similar to my problem except I dont get a blinking cursor and I don't use an ssd. I tried the "add 2 seconds delay" trick from the article but it didn't make any difference.

So at the moment I am stuck with GDM. 

I am looking for help and instructions on how to get lightdm working again. Are there any special config files or log files I could look at? Any other suggestions I can try?

Thank you for reading!

EDIT:

I have come to the conclusion that lightdm is simply not compatible with the nvidia drivers (atleast the newer ones). When the nvidia drivers are **installed** lightdm wont work, but gdm does. However, when the nvidia drivers are **uninstalled** both lightdm and gdm works.

---

### Post by deadflowr on 2014-12-16
Do you have BOTH bumblebee and nvidia-prime installed?

---

### Post by tobbe.bia on 2014-12-16
> **deadflowr said:**
> Do you have BOTH bumblebee and nvidia-prime installed?

No, only bumblebee.

---

### Post by tobbe.bia on 2014-12-18
Any ideas?

---

