---
title: "Usplash reconfiguring wrong boot image"
date: 2006-10-30
forum: General Help
---

### Post by CheeseEatingBulldog on 2006-10-30
I recently updated to edgy, and with some minor hiccups I have got it to run,  with xgl/beryl to boot. 

Anyway, when I boot I do not see a usplash (cannot find usable theme 1280x1024). So I changed the usplash config to 1024x768 (manually in file) and now it does show the usplash when shutting down, but not when booting up. So, my assumption was that usplash had to be reconfiged (dpgk-reconfigure usplash), so that it would update my initrd.img for booting.

Only it updates "update-initramfs: Generating /boot/initrd.img-2.6.17-10-386" 
which is not the kernel I am using (I am using the Generic kernel), but whatever I try it will not update my current initrd.img, and keeps on updating the wrong one.

Anyone have an idea why? or how I can force it to update the right one?


==> Edit

I solved the problem by update-initramfs -u -k [KERNEL VERSION] now I have usplash on both shutdown and startup :D

---

### Post by lrrr on 2006-12-08
I've been trying to make my own usplash theme, and I ran into the same sort of trouble as you did. [The theme was displaying correctly, but not with my changes.] But update-initramfs fixed the problem. Thanks Bulldog.

---

