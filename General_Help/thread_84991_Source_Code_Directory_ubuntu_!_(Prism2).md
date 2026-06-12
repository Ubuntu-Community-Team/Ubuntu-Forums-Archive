---
title: "Source Code Directory ubuntu ?! (Prism2)"
date: 2005-11-01
forum: General Help
---

### Post by cydec on 2005-11-01
Noob talking here, sorry for the question!

I downloaded Prism2 ("linux-wlan-ng-0.2.1-pre26") - unpacked it to "/usr/src" - then i tried to run the "./Configure" - i typed "y" on the usb because it is a usb wlan adapter, but intern ("Z-Com XI-726 wlan adapter).

But after i selected y on the usb adapter the configure asks me to give "The Linux Source Directory" (He automaticly enters: "/lib/modules/2.6.12-9-386/build") whe he tries to go further it fails because he tells me it is incomplete or missing .... (there isn't even a build folder and the parent as input won't work)

what in godsname (;-)) is the Linux source directory ?

i tried to download the linux kernel on kernel.org and unpacked it and gave it as source directory but still won't work.

I'm only trying to get my Z-Com xi-726 to work ... yeah i'm only a noob, please help me out here.

---

### Post by teaker1s on 2005-11-01
just some suggestions
sudo apt-get build-essential-without this and it's libaries you will not successfully compile

when you did ./configure did you check that all dependancies were okay as it shouldn't 'make' if they're missing but if it did then you'll get problems
I believe if you 'cd' to the directory in console and type 'sudo make uninstall' and un install it and ./configure again you'll see missing dependancies.

as a beginer too I'm not suggesting I know the answer but this is a possible easy check to do

---

### Post by teevee on 2005-11-01
linux-wlan-ng is already included in Ubuntu. Open Synaptic and search for it. Or is there a specific reason why you need to compile it yourself?

---

### Post by az on 2005-11-01
You need linux-wlan-ng for the usb prism2 devices.  The pci and pcmcia devices use orinocco drivers, I think.  there are three different drivers that work with the prism2 chipsets (hostap is the third)


Once you install the linux-wlan-ng package (it is on the cd) you should be able to configure the usb device with the networking tool.  If this is not the case, add to this bug report about that:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)


If it is not a usb device we are talking about, show the output of 
lsmod

---

### Post by mo_x on 2005-11-01
You also need to install the linux-headers-2.6.12-9-386 package.

---

### Post by cydec on 2005-11-02
Thanks for all your help people.

Indeed, stupid of me, i didn't need to compile it from scratch.

A) I just installed linux-wlan-ng with the use of Synaptic.
B) Installed the Windows drivers with the use of ndiswrapper.

Case Solved after config and activation of my WiFi.

---

