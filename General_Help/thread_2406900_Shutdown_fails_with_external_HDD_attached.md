---
title: "Shutdown fails with external HDD attached"
date: 2018-11-27
forum: General Help
---

### Post by MoebusNet on 2018-11-27
I'm not sure the Desktop Environment matters for this question, but my notebook running Lubuntu 18.04 32-bit with current updates with my 5GB USB3 external HDD (DC powered from wall socket)  attached via USB2 (no USB3 on motherboard) when I choose Menu>Logout>Shutdown the screen goes blank but Shutdown does not complete and the external HDD remains powered. To get the notebook to shutdown, I must dismount all external HDD partitions in PCManFM then physically unplug the external HDD's USB cable from the notebook's USB port. Only then will the external HDD and the notebook power down. Google does not list this issue for *buntu 18.04, only scattered references to previous versions. Where would I look for logs to diagnose this?

---

### Post by MoebusNet on 2018-11-28
The funny thing is, running Lubuntu 18.04 64-bit with current updates with the same external HDD via USB3 on my newer notebook does not result tin the same problem. Could this be a timing issue where the USB2 interface is too slow for the shutdown process with a (relatively) large HDD?

---

### Post by MoebusNet on 2018-11-30
Ideas? If this is a bug, what process-name would I use to file the bug under?

---

### Post by MoebusNet on 2018-12-01
Well, the updates of the last four days seem to have remedied the shutdown-with-external-HDD-attached issue. Hopefully it will stay fixed for a while. BTW, I should have stipulated that this is a backup external-HDD, rather than a dual-boot system with Ubuntu installed to the external HDD. Thanks for all the fish (or should I say *fixes)*!

---

