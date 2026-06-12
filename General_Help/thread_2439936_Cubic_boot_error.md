---
title: "Cubic boot error"
date: 2020-04-03
forum: General Help
---

### Post by Redalien0304 on 2020-04-03
Have Cubic Installed Ubuntu 18.04. Trying Customize Ubuntu 20.04 Cinnamonremix ISO. An Unofficial Ubuntu Flavor
Get "**loading /casper/intrd.lz failed no such file or directory**" on trying to Boot from Usb.
Noticed that there is not Pressed file. Tried with Ubuntu 18.04 works good.
I know that the Ubuntu 18.04 Official version is Different than What i am trying to do with Ubuntu 20.04 Cinnamonremix

Any help or Advice is Appreciated.


Ubuntu 20.04 Cinnamonremix ISO
[https://twitter.com/UbuntuCinnamon](https://twitter.com/UbuntuCinnamon)

---

### Post by sudodus on 2020-04-03
Try looking for [FONT=Courier New]**/casper/intrd**[/FONT]

In other words I think there should be no [FONT=Courier New]**.lz**[/FONT] extension of initrd.

---

### Post by Redalien0304 on 2020-04-03
i have tried that still get error **l****oading /casper/intrd.lz failed no such file or directory**&#8203;

---

### Post by sudodus on 2020-04-04
I see. Have you checked where the vmlinuz and initrd files are located in the iso file? You can check, by loop mounting the file, something like the following,

```

sudo mount -o loop filename.iso /mnt
find /mnt -name "*vmlinuz*"
find /mnt -name "*initrd*"

```

---

### Post by Redalien0304 on 2020-04-04
I think i have Solved it, i think I Renamed initrd in /Casper i believe? Cubic was not Changing it for some reason? So i did Sudo Root into the Project Dir.

---

