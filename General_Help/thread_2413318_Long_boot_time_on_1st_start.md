---
title: "Long boot time on 1st start"
date: 2019-02-24
forum: General Help
---

### Post by technano on 2019-02-24
Hi,

I have successfully installed Ubuntu 18.10 on my Windows laptop. So far so good. However, on the 1st boot up, select Ubuntu (from Grub), strangely it display nothing for a long time. I waited for 1-2mins and decide to press Power button to force shut down the machine and restart the phone. Yet, on the second start up, after selecting Ubuntu (from Grub) it boots straight into Ubuntu 

Currently, it is dual-boot with Windows 10

I don't think the problem lies with the hardware. 

2nd gen i7
8GB 
SSD

Would appreciate any comments and suggestions. 

Thanks!

---

### Post by oldfred on 2019-02-24
First do not shut down with power switch unless that was only option after a long time. One user just posted first boot seemed to run fsck which took a couple of hours.
Always do this first or you may corrupt file system and have to run fsck:
       Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 

What video card/chip?

What does this show?
      
 systemd-analyze

---

