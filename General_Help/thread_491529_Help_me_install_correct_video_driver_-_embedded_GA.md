---
title: "Help me install correct video driver - embedded GA-946GMX motherboard"
date: 2007-07-03
forum: General Help
---

### Post by crafter on 2007-07-03
Hi all. First post. Sorry it has to be a call for help!

I recently purchased a new computer with a Gigabyte GA-946GMX motherboard, which has a built in graphics adapter.

I installed Ubuntu 6.06 LTS successfully. However, my video installation is not optimal. It seems that my graphic adapter is unrecognisable, and I'm not sure how to proceed.

Just a few notes to aid you:
- Only the vesa driver seems to be working if I manually edit the xorg.conf or use 'dpkg-reconfigure xserver-xorg'

- lspci -v gives no mention of my display

- I installed the 915 resolution package, and running '915resolution -l gives the message "Intel chipset detected.  However, 915resolution was unable to determine the chipset type."

- Running lshw gives the following output
> - sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@00:02.0
       version: 02
       size: 256MB
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:f2000000-f20fffff iomemory:e0000000-efffffff ioport:c000-c007 irq:12

- (extract of) Dmesg gives 
> [17179569.840000] Boot video device is 0000:00:02.0
[17179570.296000] vga16fb: initializing
[17179570.296000] vga16fb: mapped to 0xc00a0000
[17179570.388000] Console: switching to colour frame buffer device 80x25
[17179570.388000] fb0: VGA16 VGA frame buffer device


- My resolution seems fixed and I;m unable to change it. and I can't use programs that require grapohic acceleration. The font quality is also very poor.

Please help me install the correct video driver for my machine.

---

### Post by coldstatue on 2007-07-04
I can't be sure, but here is a suggestion from a newb. I was helping someone else with a laptop that had no widescreen res, and also the other probs you mentioned. I was told to do this

```
sudo aptitude install xserver-xorg-video-intel
```

It fixed everything. 

Have you installed the fontsets available in... I think automatix? (I'm away from an ubuntu box right now. Can't check.)

---

### Post by coldstatue on 2007-07-04
btw, about 90% of my posts here are calls for help. There's always someone happy to help, and they are always much more knowledgable than I. I am sure you will get some more posts here.

---

### Post by kvonb on 2007-07-04
I would suggest trying Feisty (Ubuntu 7.04), you might find that it supports your later hardware a bit better.

---

### Post by crafter on 2007-07-04
Thanks

I'm probably going to need both pieces of advise.

The xserver-xorg-video-intel packeage seems to be available only for later than Dapper. this link says so:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

However, re-installing is not an easy thing to do. I don't have access to a great broadband connection and so an online upgrade of +- 600 M is out of the question for me. I can't download the install iso's (bandwith-challeged) and I beleive that if I order the CD's though shipit, I won;t be able to updrade, just do a clean install. 

I still need to find a solution for dapper, at least until I am able to upgrade. Or if I can do a partial updrage (that is, not have to updrade each packade that is installed, I may be able to swing something.

---

