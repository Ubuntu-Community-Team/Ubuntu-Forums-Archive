---
title: "Installing Nvidia Drivers???"
date: 2008-05-22
forum: General Help
---

### Post by mynameisbrett on 2008-05-22
Hello,

I'm new to Ubuntu (and much of Linux in general).

I would like to setup this new partition to be a working Desktop. Unfortunately, I've had problems before installing distributions on my computer due to my GFX Card which is a Nvidia 6150 LE (an onboard card)

How would I go about installing the drivers for this card and then installing a desktop environment?

I apologize for the newbness of the question, but if you can link me to any site that could help me or hook me up with any advice I'd be pretty grateful. I've been searching the forums, but haven't found much that would give me a more direct answer.

---

### Post by tamoneya on 2008-05-22
for almost all nvidia cards you can install it through the restricted driver manager (system -> administration -> hardware drivers).  If that doesnt work you can use a program called envy which fixes almost any graphics card driver problem.

---

### Post by Azraelthe7th on 2008-05-22
Hey brett.  Your card should work "out of the box", as the installer should detect it and fetch the latest drivers for it.

I do recommend getting Envy (or EnvyNG, which is found in the Universe repositories in the Synaptic Package Manager).  It's a tool that fetches the latest available NVIDIA or ATI drvers, installs them and sets up the X server via a graphical interface.

---

### Post by warp99 on 2008-05-22
Install Ubuntu like you normally would then when the system reboots press the escape key to enter the grub menu and choose recovery mode. Boot to a root prompt to install the following:

```
sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx
```

after that issue a 'reboot' command and Ubuntu should be using the new drivers. If not just enable the drivers in the restricted drivers manager. 

Of course you need an internet connection to do this so i would suggest you make sure it's working when you first boot to the install disc.

---

