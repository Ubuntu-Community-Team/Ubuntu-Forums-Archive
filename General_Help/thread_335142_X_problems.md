---
title: "X problems"
date: 2007-01-09
forum: General Help
---

### Post by gorded on 2007-01-09
After updating to the new xserver-xorg-core after rebooting i can get to the the login prompt but when the window manager loads X crashes and then restarts.

I am using the lastest nvidia driver 9746 at first i thought is was due to the other problem people on nividia were having but they aparently can't get the gdm to start up so i am at a loss.

Any idea?
Thanks

---

### Post by dcstar on 2007-01-10
> **gorded said:**
> After updating to the new xserver-xorg-core after rebooting i can get to the the login prompt but when the window manager loads X crashes and then restarts.

I am using the lastest nvidia driver 9746 at first i thought is was due to the other problem people on nividia were having but they aparently can't get the gdm to start up so i am at a loss.

Any idea?
Thanks

Best thing in the short-term may be to edit your xorg.conf file to use the VESA driver, at least then you can get X running to help you sort out the problem.

---

### Post by Macke800 on 2007-01-13
Hi!

I hade the same problem, everytime something tried to use the graphic cards 3d parts X restarted. I also do run 9746 of the Nvidia drivers.

I managed to get everything working normally again by reinstalling the 9746 drivers again accordingly to method 2 in this tutorial:
[http://doc.gwos.org/index.php/Latest_Nvidia_Breezy]("http://doc.gwos.org/index.php/Latest_Nvidia_Breezy")

---

