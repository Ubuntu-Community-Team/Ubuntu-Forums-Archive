---
title: "I've broken GRUB"
date: 2014-08-16
forum: General Help
---

### Post by frenchian on 2014-08-16
I had four OS on my PC. 

W7, Kubuntu and two copies of Mint (by mistake). I decided to get rid of one of the Mints, by wiping the partition then merging it into another. BIG MISTAKE. Naturally, GRUB can't find that partition, so it doesn't work.

It says it's going into GRUB rescue (?) but nothing happens.

Is there anything I can do? (This is my wife's PC, so I have access to the internet, plus installation CDs for Kubuntu and Mint, but I'd rather not start again.)

Thanks

---

### Post by grahammechanical on 2014-08-16
Do you understand the mistake that you made? The last Linux to be installed puts its Grub boot menu in charge of booting. The configuration files for Grub were in the partition that you deleted. You could have avoided this by loading into one of the other Linux OS and running.

```
sudo grub-install /dev/sda
sudo update-grub
```

and that would have put that particular Linux in charge of the boot menu. Two things to try. Load a live session and open the File Manager. That should mount the file system. Then open a terminal and run those two commands. Or use Boot Repair. A utility especially for repairing Grub.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Regards.

---

### Post by frenchian on 2014-08-16
Yep, I realise now. I might have got away with it if I'd removed the first Mint install, but my luck doesn't run that way...

I fixed it with Boot Repair, Not easily - I couldn't get a terminal to accept any of my commands - but managed it somehow.

Thanks for the advice - your approach sounds like a neat solution - hopefully, I'll never need to use it, or Boot Repair, again!

Cheers

---

