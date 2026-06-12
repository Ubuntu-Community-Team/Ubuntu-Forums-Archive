---
title: "Instabilities after fresh install (ati 7850, Sandybridge)"
date: 2012-10-26
forum: General Help
---

### Post by owenww on 2012-10-26
Hi All,

I have been using Ubuntu regularly through VMWare and finally decided to install it directly.

My hardware spec is an intel sandybridge (quad core, 3.3ghz) with an ati 7850. ([This is my full spec, with an ssd and 7850]("http://www.overclockers.co.uk/showproduct.php?prodid=FS-213-OE")

Using 12.10 64bit. 

The installation went fine, but I am running into some huge problems with the UI making Ubuntu unusable. I have updated all packages but not touched any other settings.

The problems I am getting are when I have more than one window open (EG Firefox and a folder of files) I cannot click on any UI elements (Buttons, menus) and i cannot drag windows around. I can use Tab on the keyboard to highlight buttons and space to press.

I have tried using the ATI driver through 'proprietary hardware' window, but this made things worse.

I tried a fresh install and instead installed the ATI drivers from ATI's website, even worse (garbled display).

Does anyone have any idea what may be causing my issues?

---

### Post by dino99 on 2012-10-26
purge the actual installed video driver, then add the xorg-edgers ppa, and use its ati driver.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

note: after that ppa activated, update, and only install xserver-xorg-video-ati, then deactivate that ppa and update again to clean the cache.

---

### Post by sauen on 2012-10-28
[http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2]("http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2")

I just downloaded this patch, extracted it and ran the .sh script as root. I rebooted and the problem was solved.

---

