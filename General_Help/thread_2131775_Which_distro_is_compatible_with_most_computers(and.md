---
title: "Which distro is compatible with most computers?(and other usb questions)"
date: 2013-04-02
forum: General Help
---

### Post by thefederer1 on 2013-04-02
[COLOR=#333333][FONT=arial]I installed Ubuntu 12.10 on my 8gb usb and it loads very slowly on my desktop, then the screen continues to flicker, is this because I use a Nvidia gtx 550 Ti? On my inspiron dell laptop it loads, although it doesn't allow me to search wifi networks. I tried it again at school but got an error saying the kernel was incompatible with the processor because it didn't support pae. This confused me the most because it is an intel i5 like my desktop at home, although at school I think it is an older version (my desktop is ivy bridge).[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]Would it be better to use a different distro that is compatible with more computers ? [/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Do I need to install graphics/wifi drivers to get it to work on my computers at home?
[/FONT][/COLOR]
This is the site I used to create my usb key [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
[COLOR=#333333][FONT=arial]If you have any answers to my above questions, I implore you to share your knowledge as I am new to linux, but would like to learn. Thank you[/FONT][/COLOR]

---

### Post by ManamiVixen on 2013-04-02
Technically, Ubuntu is the most compatible desktop of all Linux Distros. As to the Graphics, install the nvidia driver. You can select it in the "Software Sources" window on the "Additional Drivers" tab. The school PC likely wants a 64Bit version of Ubuntu, 32Bit needs PAE which is neglected on modern CPU's. Wireless may be found in the same "Additional Drivers" tab. I hope I helped.

As to other Distros, there is Linux Mint which is more friendly, but still Ubuntu Based. there is Fedora with great network support but takes time and work to set up, OpenSUSE is rock stable, but finicky in my tests.

---

### Post by mörgæs on 2013-04-03
> **ManamiVixen said:**
> The school PC likely wants a 64Bit version of Ubuntu

A 64 bit computer normally runs a 32 and a 64 bit Buntu equally well, though there is a difference in performance. Only problems related to UEFI / Restricted Boot can force people to choose 64 bit. 


> **ManamiVixen said:**
> 32Bit needs PAE which is neglected on modern CPU's.

PAE is available on all 32 bit computers younger than around 15 years with very few exceptions.

---

