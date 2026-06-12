---
title: "The official instructions for installing Ubuntu into VirtualBox don't work"
date: 2022-07-26
forum: General Help
---

### Post by xarlien on 2022-07-26
Hello, there is an official guide on [https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview) on how to properly start UBUNTU in Virtualbox. Unfortunately it doesn't work (if we are talking about current versions of Ubuntu 22.04LTS and Virtualbox 6.1.36 on W10 all 64bit).


First of all, in point #4, the installed Ubuntu will not boot with VboxSVGA graphics (black screen) - you need to revert VMSVGA immediately after installation.


And then it can't install Guest Additions at all according to the instructions (I finally stuffed it in manually with sudo apt-get install virtualbox-guest-x11), before that I tried to install dkms and linux-headers according to other instructions, I just don't know if it had any effect)


So I have a question, what is the correct procedure for installing the current UBUNT into Vitualbox?

---

### Post by ActionParsnip on 2022-07-26
[https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#4-changing-the-window-resolution](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#4-changing-the-window-resolution)

At the bottom of the guide it says "suggest changes". Click that

---

### Post by SeijiSensei on 2022-07-26
Don't switch to VboxSVGA before installation. Let VBox use whatever driver it wants. Then shut down the VM, go to its settings, and change to the SVGA adapter. VBox will complain about an "invalid" setting. Ignore it and save the changes. Now boot the machine; you should get the correct range of resolutions.

DK if that will help with the Guest Additions.

---

### Post by xarlien on 2022-07-28
For installation can be VM in VMSVGA (by default). For good working past installation must be installed VBOX GuestAdditions. Guest Additions must be installed via terminal and SUDO (plus some dependencies). Automatic "mountandrun" (as in manual) cannot work in Ubuntu. I dont understand, who make this nonworking manual. :-(

But this is only my way, not answer to my question (what is the correct procedure for installing the current UBUNTU into current Vitualbox).

---

### Post by miguel001 on 2022-07-28
I installed 22.04 to virtual box (VB) pre-release without a single issue. It was self evident how to do it so not sure what to say. Make sure you are using a compatible version of VB as that's the single most important thing.

---

