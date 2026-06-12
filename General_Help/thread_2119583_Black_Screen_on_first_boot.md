---
title: "Black Screen on first boot"
date: 2013-02-24
forum: General Help
---

### Post by jared1990 on 2013-02-24
I successfully installed lubuntu 12.04 alternate iso to my pc without error. During the first boot the LUBUNTU loading screen do appear. However after the loading screen, It went black screen the whole period of time. What should i do to fix this?

My PC Specs

Processor: INTEL PENTIUM 4 CPU 2.66GHZ
Chipset: Intel i845G
RAM: DDR1 256MB
GPU: Intel(R) 82845G/GL/GE/PE/GV Memory: 64 Mbytes
Display: 1024x768

---

### Post by matt_symes on 2013-02-24
Hi

You could try using the nomodeset switch on the grub command line.

Intel also have Linux drivers for it on their download page.

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=Intel%28R%29%2082845G/GL/GE/PE/GV&OSVersion=Linux*](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=Intel%28R%29%2082845G/GL/GE/PE/GV&OSVersion=Linux*)

Maybe that will work for you.

Kind regards

---

### Post by jared1990 on 2013-02-24
Hi thanks for the info. I just did the nomodeset that you've told me and I was able to boot in Lubuntu loading screen, but this time I 
got stuck on that screen. it does not load whatsoever. How am I going to install the driver then by the way?

---

### Post by matt_symes on 2013-02-24
Hi

A number of people have had a blank screen on boot today, with intel chipsets as well. I wonder if there was an update that caused this.

I would use a ppa and not those drivers i linked to update your system. I put that link there to show you there were new drivers availiable.

These are the xedgers ppa. very new drivers can be a bit buggy.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

This is older but should be more stable.

[https://launchpad.net/~glasen/+ppa-packages](https://launchpad.net/~glasen/+ppa-packages)

You install then like any ppa. They may fix it for you.

If there was an update recently you could always try rolling back to the previous driver.

Another thing to try. Do you still get a blank screen of you boot into an older kernel ?

Kind regards
.

---

### Post by jared1990 on 2013-02-24
Hi

Im sorry, I am just new to Lubuntu and I dont have any background of linux/ubuntu os too. I dont have any idea of those technicalities you've mention, but I am willing to learn though. How do I install those ppa then? thanks

---

### Post by matt_symes on 2013-02-24
Hi

Try this first. Another thing to try. Do you still get a blank screen of you boot into an older kernel from the grub menu ?

From the terminal for [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

```
sudo apt-add-repository ppa:glasen/intel-driver
``````
sudo apt-get update
``````
sudo apt-get install xserver-xorg-video-intel               
```and for the xedgers/drivers

```
sudo apt-add-repository ppa:xorg-edgers/ppa
``````
sudo apt-get update
``````
sudo apt-get install xserver-xorg-video-intel
```Pick one and give it a try. If it does not fix the then we will need to look elsewhere.

Remove any nomodeset setting you may have.

Kind regards

---

