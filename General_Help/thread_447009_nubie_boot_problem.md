---
title: "nubie boot problem"
date: 2007-05-17
forum: General Help
---

### Post by dfpd62 on 2007-05-17
Hi Folks

a recent electrical storm caused a power outage, and my 2 month uptime came to an end.

On reboot, all i get is a GRUB error message "error 17 : cannot mount selected partition.

press enter and an options screen offers 
  "Ubuntu, KERNEL 2.6.17-11General"
  "Ubuntu, KERNEL 2.6.17-11Recovery"

choosing any option returns to previous message.

 My box has 2 IDE Drives, 1st ide has Freebsd, running LILO which gives me the option to boot BSD or Drive 1,
which runs Grub to start Ubuntu 5.10 breezy.

Obviously the power-cut corrupted something, but what?
I have Knoppix CD if this can help repairs.


thanks in advance

Donald

---

### Post by spamking2000 on 2007-05-17
Try this... boot from the Knoppix CD, them try to mount the ide hard drives. If they mount and you're able to get to all the partitions, unmount them and run fsck to check if the drives are clean. Sounds to me like you probably have one of two problems... either the power outage killed one of your drives, or corrupted your menu.lst in grub on your boot partition.

If the drives come back clean, then you'll need to look at your settings for LILO and GRUB.

---

### Post by dfpd62 on 2007-05-19
Thanks Friend

BSD  and Knoppix boot fine, can mount and view all Ububtu (Kbuntu actually) folders and Partitions.
Next task is to unplug the BSD disk and set about learning how to repair Grub.

 ( I had a nightmare to get dual-boot setup, using LILO to start Grub is the only way that worked and I am not prepared to risk Grub intefering with disk1)

any grub help appreciated :)

Thanks again

Donald

---

