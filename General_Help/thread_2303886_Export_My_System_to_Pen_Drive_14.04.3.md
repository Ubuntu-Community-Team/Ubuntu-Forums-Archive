---
title: "Export My System to Pen Drive 14.04.3"
date: 2015-11-22
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-11-22
Hello,

I would like to export my entire configuration to a 128gb pen drive, without having to recode from bare metal. I seem to remember there was a tool to do this; and it would export your configuration, including OS, to x-many DVDs. Then, all it would take to reload your config would be to reload these DVDs, in a certain order. I could clone; but I don't need to copy the data; just the OS, the apps, config files and bookmarks.

I think the tool was called Remastersys. This is apparently not still around.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-11-23
Apparently someone is still maintaining Remastersys; so I installed it.

[https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys](https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys)

```
sudo remastersys dist
``` just copied the bare 14.04.3 distro, without any of my apps or configurations. This was a bust.

Now I'm trying

```
sudo remastersys backup
``` hoping for better results; but this copies my data, which I don't want on my pen-drive, nuts.

BTW, I tried to create the bootable pen-drive with "Startup Disk Creator," and it choked when trying to install GRUB. The iso that Remastersys created was 4.1gb. I don't know if this matters. UNetBootin succeded in creating the bootable pen-drive.

---

### Post by coljohnhannibalsmith on 2015-11-23
Yup, just like I thought; none of the switches work. It created an image with the exact same number of bits as before; so I didn't even bother trying to load it. Crud; there has to be another option. I can't wait to deploy Hannibal-Linux! BA would be so proud...

BTW, I want to keep my flashback session capability, gnome-panel launchers, desktop scripts, and the users I've created.

---

### Post by coljohnhannibalsmith on 2015-11-28
bump

---

