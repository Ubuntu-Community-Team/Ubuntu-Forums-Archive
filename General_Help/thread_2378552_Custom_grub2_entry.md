---
title: "Custom grub2 entry"
date: 2017-11-24
forum: General Help
---

### Post by jmh474 on 2017-11-24
HI all I'm abit lost as to what's going on I'm triple booting my laptop, ubuntu - windows 10 and a os called lakka, I have all os booting fine but when I select lakka from the Grub menu the screen go's blank then a new option appears on the Grub menu - 'lakka' - then I have to select this option to boot lakka is there anyway I can change this so I only have to select lakka once, I'm just trying to simplify things for my son as we love our retro games, thanks for any help

---

### Post by yancek on 2017-11-24
The Lakka site states it does "not support dual boot", whatever that mean.  I guess it works.  Have you thought about just putting it on a separate flash drive to use when you want?  Or is that what you have?
What is the entry in the Ubuntu grub.cfg menu for Lakka?  Is it a chainload entry?  Did you install Lakka after Ubuntu and run sudo update-grub from Ubuntu?
Are the windows 10 and Ubuntu UEFI installs?  Is Lakka the same?  Are all three on the same hard drive?

---

