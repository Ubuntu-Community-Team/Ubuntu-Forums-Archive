---
title: "Help with adding 2nd HDD (windows 7) to an Ubuntu installation on HDD 1"
date: 2014-07-01
forum: General Help
---

### Post by mousecalls4u on 2014-07-01
Is this possible?  I have 2 HDD slots on my laptop, I have Ubuntu 14.04 installed on a HDD now.  Can I add another HDD and install windows 7 on it and make it play nice with my initial Ubuntu HDD?

---

### Post by yancek on 2014-07-01
Install windows 7 on the second drive, put its bootloader in the master boot record of that drive and select which operating system to boot by selecting the drive from the BIOS on boot.  You could also update grub from Ubuntu after installing windows on the other drive and have an entry in the Grub menu for windows.

---

### Post by mousecalls4u on 2014-07-10
> **yancek said:**
> Install windows 7 on the second drive, put its bootloader in the master boot record of that drive and select which operating system to boot by selecting the drive from the BIOS on boot.  You could also update grub from Ubuntu after installing windows on the other drive and have an entry in the Grub menu for windows.
Thank you for the reply..

If I already have windows installed on the other drive..and all I need to do is throw it in the 2nd hdd location on the laptop, can I modify grub on my primary (ubuntu hdd)?

here's some more info... the windows drive has grub on it as I initially tried to add the ubuntu drive as a secondary drive.  I had some issues and decided to only run ubuntu so I put the ubuntu drive in the master slot and removed the windows drive.  Do I need to remove grub from the windows drive and then modify grub on the linux drive?

---

### Post by grahammechanical on 2014-07-10
How was it able to boot? If Grub was not installed on the Ubuntu drive and the Ubuntu drive was the only hard disk in the machine, then Ubuntu would not have loaded. It does not matter which drive is the primary drive or the secondary drive. If we can alter the boot priority to boot into the Ubuntu drive then we can run

```
sudo update-grub
```

That should detect the operating systems on both drives. Then we will get a Grub boot menu that offers us Ubuntu and a Windows boot loader as a choice.

Regards.

---

