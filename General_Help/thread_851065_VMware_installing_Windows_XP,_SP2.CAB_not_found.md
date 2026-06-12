---
title: "VMware installing Windows XP, SP2.CAB not found"
date: 2008-07-06
forum: General Help
---

### Post by ludatha on 2008-07-06
Hi, I am trying to install windows XP as a virtual machine so I can run Photoshop, and when I install I get an error.

> The following value in the .SIF file used by Setup is corrupted or missing:

Value 0 on the line in section [SourceDisksFiles]
with key "SP".cab."

Setup cannot continue. To quit Setup, press F3.

I've looked on the internet and to solve the problem I need to change my bios to boot from the cd, but I am trying to install it on a Virual Machine...

Any Ideas?

I have tried 2 different ISO's

---

### Post by LinuxRocks713 on 2008-07-06
Actually, you need to configure the virtual BIOS to boot from CD. You can edit that easil in VMware Server 1.x by clicking properties.

Your SP2.CAB file is either caused by (two) scratched CDs; It has nothing to do with VMware. Also consider running Wine([http://www.winehq.org/](http://www.winehq.org/)) for just Photoshop.

---

