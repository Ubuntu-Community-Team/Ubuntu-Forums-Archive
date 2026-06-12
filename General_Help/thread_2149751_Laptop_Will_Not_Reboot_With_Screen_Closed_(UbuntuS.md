---
title: "Laptop Will Not Reboot With Screen Closed (UbuntuServer)"
date: 2013-05-29
forum: General Help
---

### Post by AwesomeMarioFan on 2013-05-29
Hello,

I have setup a home server running Ubuntu Server 12.04.2 LTS, and I would like to be able to reboot it remotely
with the command 'sudo reboot'.

However, upon running this command, the laptop will shut down, reboot, and get stuck and hang on the Grub boot screen even if there is
a timer setup. This only happens when the laptop's screen is closed, everything reboots fine when it is opened up.

I would like to solve this so the screen does not have to be open all the time.

Thanks in Advance!,

~ AwesomeMarioFan

---

### Post by AwesomeMarioFan on 2013-05-30
Anyone?

---

### Post by papibe on 2013-05-30
Hi AwesomeMarioFan.

That used to happen to me on 10.04 so I had to shutdown, and then use Wake-On-Lan to turn it back on. Luckily for me,12.04 fixed it, and now 'reboot' works fine. 

Have you try looking on the BIOS for any power saving option?

Just a thought.
Regards.

---

### Post by AwesomeMarioFan on 2013-05-30
> **papibe said:**
> Hi AwesomeMarioFan.

That used to happen to me on 10.04 so I had to shutdown, and then use Wake-On-Lan to turn it back on. Luckily for me,12.04 fixed it, and now 'reboot' works fine. 

Have you try looking on the BIOS for any power saving option?

Just a thought.
Regards.
Hi,
Thanks for responding! I checked the BIOS, and I only see a LAN power saving (I kept this at default since it seems to cause problems with keeping the Ethernet card on after shutdown).

---

