---
title: "Very slow/choppy video brings whole system to a crawl"
date: 2016-02-18
forum: General Help
---

### Post by neemo69 on 2016-02-18
Did a fresh install of 14.04 on virtualbox and installed guest additions When watching videos from  youtube or other sites they run very  choppy and brings the whole system down to a crawl. I did the ubuntu-restricted-extras for the codecs. I Have 256mb video ram allocated in vbox  settings, 5gb of system ram  allocated to this guest machine as well. I do have 3d acceleration  enabled. Anything that I should take a look at?

---

### Post by mörgæs on 2016-02-19
Hi, welcome to the fora.
Which graphics processor do you use?

---

### Post by neemo69 on 2016-02-20
Graphics card is an Asus Radeon HD7750.

---

### Post by ik-0 on 2016-02-20
run the following and post the result.

$ glxinfo | grep -i render
$ lsmod | grep radeon
$ lsmod | grep fglrx

The first one will tell you if you are using direct rendering (aka hardware acceleration)
THe second will tell you if you are using the radeon open source driver.
The last one will tell you if you are using the fglrx closed source driver from AMD.

You might need to install the fglrx driver from the software sources program
$ software-properties-gtk
THen go to the additional drivers tab.

---

### Post by neemo69 on 2016-02-20
> **ik-0 said:**
> run the following and post the result.

$ glxinfo | grep -i render
$ lsmod | grep radeon
$ lsmod | grep fglrx

The first one will tell you if you are using direct rendering (aka hardware acceleration)
THe second will tell you if you are using the radeon open source driver.
The last one will tell you if you are using the fglrx closed source driver from AMD.

You might need to install the fglrx driver from the software sources program
$ software-properties-gtk
THen go to the additional drivers tab.

1. Resutled in this: "The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils"
2nd and 3rd command didnt bring up anything or display anything, just went to a new terminal line.

---

### Post by ik-0 on 2016-02-20
Sorry - I didn't realize it's in VirtualBox.  fglrx/radeon won't be installed.  Do you have VBox guest additions installed?  Make sure you have vtx enabled in your BIOS.

---

### Post by neemo69 on 2016-02-24
Yes vbox additions are installed, and virtualization enabled in bios.

---

### Post by QIII on 2016-02-24
No matter what you do, the graphics performance of any guest will be terrible.  VirtualBox uses a hardware abstraction layer, which means that the guest OS runs on virtual hardware presented by the virtualization software -- and that is terrible.

---

