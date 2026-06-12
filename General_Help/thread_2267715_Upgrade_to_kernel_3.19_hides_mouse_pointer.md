---
title: "Upgrade to kernel 3.19 hides mouse pointer?"
date: 2015-03-03
forum: General Help
---

### Post by eezacque on 2015-03-03
I upgraded to kernel 3.19, but lost my mouse pointer.
The mouse is still functioning, just don't see its pointer, which makes the system pretty much useless.
Any clues?

Also, upon boot, I see *'**ACPI* PCC *Probe* Failed'?

---

### Post by grahammechanical on 2015-03-03
What version of Ubuntu are you using? I am using Vivid Vervet. It is the development branch of the next release of Ubuntu (15.04). The kernel team have only recently put kernel 3.19 into the vivid archives. Today is the first time I am using it. This is what the kernel team say about kernel 3.19

> [COLOR=#333333][FONT=UbuntuBeta]We have officially uploaded our v3.19 kernel for Vivid to the archive, [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuBeta]ie. 3.19.0-7.7. Please test and let us know your results.[/FONT][/COLOR]

[http://voices.canonical.com/kernelteam/2015/03/03/kernel-team-meeting-minutes-march-03-2015/](http://voices.canonical.com/kernelteam/2015/03/03/kernel-team-meeting-minutes-march-03-2015/)

Are you using a proprietary video driver? If you are not on Vivid Vervet and you are using a proprietary video driver then I suggest that you switch to an open source video driver.

A couple of weeks ago I installed an early version of kernel 3.19 (release candidate) and also kernel 4.0 (release candidate). Both loaded to a low resolution screen when using a proprietary video driver but not with an open source video driver. By waiting for the kernel to be put in the archive I received a 3.19 kernel that works with my proprietary video driver.

The kernel team have until 09 April to fix anything that is faulty with the 3.19 kernel. So, kernel 3.19 should be considered experimental until 15.04 is released. Ubuntu 14.04 will not get kernel 3.19 back ported until 3 months after 15.04 is released. 

Are you using a default Ubuntu theme? That could be another area to investigate.

Regards.

---

### Post by eezacque on 2015-03-03
> **grahammechanical said:**
> What version of Ubuntu are you using? I am using Vivid Vervet. 


I am using Ubuntu 14.10

> 
Are you using a proprietary video driver? If you are not on Vivid Vervet and you are using a proprietary video driver then I suggest that you switch to an open source video driver.


No.

> 
The kernel team have until 09 April to fix anything that is faulty with the 3.19 kernel. So, kernel 3.19 should be considered experimental until 15.04 is released. Ubuntu 14.04 will not get kernel 3.19 back ported until 3 months after 15.04 is released. 


I am using kernel 3.19, hoping it will fix my Ubuntu hanging every few weeks ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1384342](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1384342))

> 
Are you using a default Ubuntu theme? That could be another area to investigate.


Yes, I am using a default theme.

---

### Post by harmti on 2015-03-19
[COLOR=#000000]*I have Vivid Vervet on Lenovo t440s, ubuntu-gnome, pretty much vanilla setup. Mouse pointer is visible, but it does not change, always fixed to the same black arrow with white line. Makes it hard to resize windows. I'm not exactly sure, but I think this started around the time I got 3.19 kernel. *[/COLOR]

---

