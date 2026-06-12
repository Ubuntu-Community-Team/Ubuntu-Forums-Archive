---
title: "graphic driver problem"
date: 2021-10-05
forum: General Help
---

### Post by jgw on 2021-10-05
I have been having display prolems on my computer (not this one).  The problem is that stuff seems to go crazy pages I am not on but are on my screen.  I decided it was my driver.  I went to software & updates, went to additional drivers.  I have an nvidia card and was using the open source driver and the nvidia driver was available (I think it was 340).  Anyway, I checked that one and so it proceeded to install it.  It went on for some time and then, eventually, it came to a halt, said it had installed it but there was a problem.  I re-started my machine and it booted up to a black screen.  

My thought was to boot back up with the cd that I used to install the current 20.04.3    I got that up and the driver was the open source driver but that was for the boot off the cd.  I have no idea how to change it on the system itself and assume that is still using the failed nvidia program and I want to change that but I am clueless.  

Can anybody help me?

Thank you..................

---

### Post by grahammechanical on 2021-10-05
At the Grub boot menu select Advanced Options for Ubuntu. Then select a Linux kernel with recovery mode. At the recovery screen select Resume. This system will load using a low resolution open source video driver. At least you will be at a working desktop. Now you can access Software & Updates and deactivate the Nvidia driver. A reboot should load Ubuntu using the standard open source video driver as before.

Regards

---

### Post by jgw on 2021-10-05
Thanks for the reply!

I also rooted around on the net and did:
sudo  systemctl  stop  lightdm.service
sudo  apt  purge  '^nvidia-*'
sudo  apt  install  xserver-xorg-video-nouveau
sudo  reboot  now

And that seemed to fix it (I am back up and running and it deleted the nividia driver v340.108 (which is now back)).   I have had problems with that driver before.  Now running the open driver which is working.  the current nvidia driver above v340.108 is what I have now.  Not sure which one was the one I deleted but I am happy to see it gone <g>

Thanks again!

---

