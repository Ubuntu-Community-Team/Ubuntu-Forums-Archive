---
title: "correct linux-source for Gutsy Gibbon?"
date: 2007-12-11
forum: General Help
---

### Post by pollyp on 2007-12-11
[Note: this is a re-post from the installation and upgrades forum. If anyone can shed light on the Gutsy kernel source versions, I'd* really *appreciate it. Thanks!]

Hi everyone,

I´ve upgraded to Gutsy Gibbon for i386 machines, but need to compile a custom kernel to enable support for my Intel HDA sound card. So I grabbed the linux-source package, which synaptic says is 2.6.22-14.46, made my changes in the config file, and compiled the image and headers and installed them. But when I boot into the new kernel, uname -a tells me that I'm running 2.6.22.9. 

Can anyone explain to me why this is? Is there a patch file somewhere that I´m supposed to apply? Or some other package I should be using? Except for the sound card, Gutsy works great for me, so I like to base my custom builds off that exact source.

All attempts at kernel building enlightenment gratefully accepted ...

---

### Post by g2g591 on 2007-12-11
um that driver is compiled in the default kernel. (i happen to have that sound card and it works just fine by default)

---

### Post by pk_sunshine on 2007-12-11
Sorry but this is not an answer but a question to the original statement:
  [PHP]  I grabbed the linux-source package[/PHP]
Can you please tell me where I might be able to download the source-code for Gutsy server version 2.6.22-14-server

I've looked...but can't find it :confused:..

---

### Post by pollyp on 2007-12-12
> **g2g591 said:**
> um that driver is compiled in the default kernel. (i happen to have that sound card and it works just fine by default)

Not on my machine, it doesn't. I have the Intel 915G chipset with a ICH6 controller, and the Gutsy image couldn't play any of my sound files, and the volume control had a big red bar through it. When I recompiled the kernel with support for the Intel HDA module, sound started working. It's been this way for me on this hardware since I did my first Ubuntu install with Edgy.

---

