---
title: "Nvidia driver problem Xubuntu 14"
date: 2014-09-16
forum: General Help
---

### Post by guccimucci on 2014-09-16
I have a Nvidia Geforce GT740m on my Dell vostro 5470.  I've been having troubles with graphic drivers. When I use  software&updates to seek for additional drivers it'll give me  several selections, but only the x-org nouveau driver works properly.  

I've tried different drivers from nvidia, but I ended up with touchpad  freeze or last time I couldn't even boot into graphical environment  after applying Nvidia drivers and had to uninstall Nvidia to get my  Xubuntu working again. It said that system encountered a problem and do I want to report it.  In details it said something about x-org file in system folder. 

The only guidance I've found so far says: "Go to "All Settings > Additional Drivers" and you should see a list  of all available nvidia drivers ready to be installed. Select the  correct driver and click Apply Changes. The new driver would be  downloaded, installed and configured for use."

But it doesn't seem to be that simple..


I am using Xubuntu 14.04. Is there a way I could get Nvidia drivers  working on my computer? I wouldn't want my computer to crash during an  important lecture or something.

---

### Post by redrumrogue on 2014-09-16
I had some issues with the proprietry drivers in the "Additional Drivers" list as well.  I can't remember exactly what issues I had because it was a few months ago but I found the only driver which worked for me (nVidia GeForce GT620 card) was the one marked as "(proprietry, tested)".  Have you tried the tested one?  Since then I decided to install the latest stable driver from nvidia website and had no issues at all.  This requires a manual install though.

---

### Post by guccimucci on 2014-09-16
I don't have such selection. I only have the one that ends with 'proprietary', but I've tried that one.

---

### Post by redrumrogue on 2014-09-16
You could try the latest stable driver from the nvidia site.  I used this guide to install mine without a problem ... [http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver)
I followed the second reply in that thread.  Be careful, if you're not sure of what it's asking you to do then probably best not to try it!

---

### Post by guccimucci on 2014-09-17
I have tried this guide, but I got stuck in the part
  update-initramfs -u

It did not do anything when I wrote it in Terminal.

---

### Post by redrumrogue on 2014-09-17
Yes, you shouldn't have to execute that command.  My understanding is that it's only necessary to do that line if your nouveau driver is built into the kernel.  Normally the nouveau driver is installed as a loadable module instead so you should just have to add the blacklist file in /etc/modprobe.d.  Did you complete the nvidia driver install?

---

### Post by cariboo on 2014-09-17
I have a newer Nvidia graphics card that isn't supported by any drivers in the 14.04 repositories. What I did, was go to Nvidia, to see what the latest driver for my GeForce GTX 750 (GM107) is. I then enabled the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") using the following commands:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

and in my case I needed the nvidia-343 driver:

```
apt-get install nvidia-343
```

I'm currently using the same driver in 14.04 and 14.10.

---

### Post by guccimucci on 2014-09-19
It seems to be working. Thanks!

---

### Post by guccimucci on 2014-09-21
Here we go again... After several days without any issues my graphical environment started to freeze again.

Suddenly I can't use my touchpad and I can only get it back by exiting the graphic environment with ctrl+alt+f6 and then I can get back with ctrl+alt+f7 and it works again. It has happened several times today and it is getting quite annoying.

What could be the problem? I did not encounter problems like this with x-org nouveau drivers.

---

