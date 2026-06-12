---
title: "Did anyone else get hosed by the last kernel update?"
date: 2006-08-05
forum: General Help
---

### Post by diamond on 2006-08-05
Well, I wasn't exactly hosed, but it gave me a hell of a scare.

I have a dual-boot system, with WinXP on /dev/hda1 ((hd0,0) to Grub) and Dapper on /dev/hda2 (or (hd0,1)). I logged on the other day to find the "Update" icon, and found that a minor update to the kernel (I'm running 2.6.15-26-386) was one of the updates. So I told it to install, and after downloading and installing everything, it prompted for a reboot.

I restarted, and Grub gave me an error saying that it couldn't find the root filesystem.

After my heart started beating again, I realized that the "root" command had been changed from "root (hd0,1)" to "root (hd0,2)". So of course it couldn't find it. I was able to change it temporarily from the Grub command line, boot into Linux, and fix the menu.lst file. Problem solved.

So in the end it wasn't a big deal, because I knew Grub well enough to work around the problem and fix it. But this concerns me, because Ubuntu has made great strides towards becoming the "newbie-friendly" Linux distro. If this had happened because I was screwing around with the system (which is not at all unknown to happen), that would be one thing. But it resulted from a standard update that I installed the usual way. A newbie would have been completely dead in the water, and may have ended up reformatting their drive to fix the problem.

Hopefully it was just something odd about my system that triggered this, but I'm curious to know if anyone else encountered the same problem.

---

### Post by FizDev on 2006-08-06
Hmm... strange, didn't happen to me. I simply upgraded and rebooted... everything working fine without any problems.

---

### Post by jimmygoon on 2006-08-06
I dunna but -26 screwed up my wireless... I have to manually choose -25 at each boot :(

---

### Post by FizDev on 2006-08-06
Maybe you could simply remove the -26 from your boot list... or remove it completely... maybe you'll be luckier with -27 ;)

---

### Post by diamond on 2006-08-06
> **jimmygoon said:**
> I dunna but -26 screwed up my wireless... I have to manually choose -25 at each boot :(

What system are you running, and what's your wireless chipset? Did you rebuild ndiswrapper after the update?

I know that wireless is very fragile on mine; the slightest system change can send it into turmoil, and a kernel update is the worst.

---

