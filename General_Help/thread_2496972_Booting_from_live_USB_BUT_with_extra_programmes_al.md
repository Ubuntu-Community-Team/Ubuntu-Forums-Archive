---
title: "Booting from live USB BUT with extra programmes already installed"
date: 2024-04-18
forum: General Help
---

### Post by tedrekasta2 on 2024-04-18
Forgive me if this is a silly question. But I do have a genuine need for this. Also forgive me I am not very competent with Ubuntu.

I do realise I can install Ubuntu onto a USB memory stick but it seems to be slower than a live distribution. I believe? live distributions load into RAM which makes them faster and I have 32Gb of ram.

Is there a way to run a live USB which has been modified to include another programme and also some chrome browser extensions? Basically I want live Ubuntu with Chrome browser plus Chrome browser extensions.

Thanks for any help it will be much appreciated.

---

### Post by dragonfly41 on 2024-04-18
Research how to create _persistent_ LiveUSB where you install extra added applications and use that as ongoing persistent LiveUSB.

Another approach is to customise the ISO you use to create LiveUSB. For this you need to use CUBIC in an existing Ubuntu session. This creates a custom ISO and feed this into LiveUSB when creating in say Rufus or MkUSB. But Cubic is really intended for major customisation. Creating a persistent LiveUSB for what you require should be adequate. Or you might add a script to auto install some apps.

---

### Post by tedrekasta2 on 2024-04-18
Many thanks but I thought that only works if you 'install' to the usb. not if you use it live. anyway i shall do as you suggest. kind regards

---

### Post by sudodus on 2024-04-18
I agree with dragonfly41: try with a persistent live system. You can use [mkusb](https://help.ubuntu.com/community/mkusb) to make persistent live systems with all current versions of Ubuntu Desktop and Ubuntu community flavours (Kubuntu, Lubuntu ... Xubuntu). It might be a good idea to run a light-weight flavour, for example Lubuntu or Xubuntu live, if you have a slow USB pendrive.

If you have a fast USB-connected SSD drive, it will be quite fast, and it will be no problem with standard Ubuntu Desktop, even if you add several program packages and even updates & upgrades.

---

### Post by #&amp;thj^% on 2024-04-18
+1 For "mkusb".

---

### Post by dragonfly41 on 2024-04-18
I would just add a note ... try a USB 3.0 port rather than USB 2.0 port. Even better if it is powered. I use powered USB 3.0 hub for multiple devices, interfaced to host PC through port on the back (nearest motherboard).

---

