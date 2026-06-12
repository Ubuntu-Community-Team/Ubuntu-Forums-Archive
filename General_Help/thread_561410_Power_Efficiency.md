---
title: "Power Efficiency"
date: 2007-09-27
forum: General Help
---

### Post by zorkerz on 2007-09-27
I have approximately 4.5 hours of class back to back this semester with no power access. This has gotten me interested in the topic of power efficiency in linux mostly ubuntu. What can I do to make my computer as efficient as possible?

I personally am running a thinkpad x61 with gutsy beta (as of today!), it has the intel gma x3100 graphics chipset, an intel ad1984 sound card, and an PRO/Wireless 4965 wireless card. I know its an intel heavy box.

Gnome power management is more basic than what I am looking for. Neither is hibernate and suspend, I pretty much use the computer straight through. Neither of these currently work for me but I believe there are solutions already on some threads here.

**Currently I have been looking at PowerTOP. It suggests a number of  things (listed below) but I do not know how to have them done by default on startup so that I do not need to open power top and keep it running all the time. Also If anyone has a good method for me to figure out what all the top causes for wakeup in PowerTOP that would be great also. **Im sorry im too long winded as usual. Thanks for the advice.
[B]
PowerTOP suggestions:[/B]
> Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config
-> how do I do this? the grub commands have always confused me a bit

> increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity
-> what does this really do?

> Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config
->are there any downsides to this and again how?

**What other things are there that I can do to improve my power efficiency?**

intel just started a new site [lesswatts.org]("http://ubuntuforums.org/lesswatts.org") which is a very cool and informative site but after going through it all I found that I either did not know enough to do most of their suggestions or did not want or feel comfortable doing most of them.

Thank you
elias

---

### Post by atlfalcons866 on 2007-09-27
you can go into your bios and turn on harddisk time out on if your bios supports it.

---

