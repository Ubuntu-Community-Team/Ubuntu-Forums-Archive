---
title: "Windows update teething problems"
date: 2015-03-26
forum: General Help
---

### Post by beth2 on 2015-03-26
I've got a main HDD with an Ubuntu install and a storage partition for windows - I normally use the grub bootloader to boot into an SSD with my windows 7 install. The recent windows update seems to have screwed everything up, and booting into windows would take 3 attempts as it tried to alter/revert changes in the registry. As of today I'm getting "error: attempt to read or write outside of disk hd0" on the grub bootloader. 

I disconnected my HDD and let windows update do its thing, and the SSD seems to be fine. However, when I plug the HDD back in I'm getting the same grub bootloader error, and if I alter the BIOS settings to boot from the SSD the windows loader comes up, but stalls halfway through startup.

---

### Post by yancek on 2015-03-26
Can you boot Ubuntu?  Do you get the Grub error only when trying to boot windows?  If you can boot Ubuntu, run:  sudo update-grub if you have not.  Otherwise, you will probably need to post more detailed information using the boot repair software, select the option to Create Boot Info Summary and post it here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2015-03-26
You said the SSD "seems to be fine", but then you later said that Windows "stalls halfway through startup".

Does Window stall even when only the SSD is connected? Or does it stall only when both drives are connected?

---

### Post by beth2 on 2015-03-27
Only when the HDD is connected. The SSD by itself seems to be fine.

---

### Post by yancek on 2015-03-27
You forgot to post the boot repair output or have you resolved the problem?

---

### Post by Mark Phelps on 2015-03-27
> **beth2 said:**
> Only when the HDD is connected. The SSD by itself seems to be fine.

My guess then, is that there is something wrong with the Windows boot stanza in GRUB -- if, when only the SSD is connected, you boot directly into Windows.

If that is true, when next you boot into Linux, open a terminal and run "sudo update-grub".  That will regenerate the GRUB configuration file.

Then, try rebooting and selecting the Windows entry to see if it works better.

---

