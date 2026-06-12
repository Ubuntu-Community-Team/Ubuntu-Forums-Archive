---
title: "ubuntu 12.04, nvidia 319, upgrade issue"
date: 2013-08-22
forum: General Help
---

### Post by ju2wheels on 2013-08-22
Hi all, I just upgraded from the nvidia 310 experimental to nvidia 319 and now my system is all messed up, weird thing is its only happening on my laptop and not on my servers with nvidia cards which is weird. After upgrading, jockey can no longer detect my nvidia card, nvidia-xconfig is missing, nvidia module shows as loaded by lsmod however nvidia-settings cant detect anything and bails.

I tried reinstalling the nvidia 319 packages but no luck.

Anyone else having similar issues?

Im running a Thinkpad w520.

Thanks,

---

### Post by Yellow Pasque on 2013-08-22
That laptop is an Optimus laptop (Intel/Nvidia hybrid graphics). You need to purge out whatever nvidia drivers you installed and follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by ju2wheels on 2013-08-22
I got it working again, stupid bios has a setting where it detects if your OS supports Optimus and switches it from Discrete to Optimus automatically (which funny enough doesnt always switch it on reboot apparently). I dont use bumblebee as im not concerned about power and always run it off the nvidia card only. It was working before with the stock ubuntu nvidia drivers through jockey, i just didnt realize the bios would auto switch the display adapter on me randomly.

---

### Post by Yellow Pasque on 2013-08-22
Oh, you're one of the lucky ones with a BIOS switch. Glad you got it working.
Please mark solved.

---

