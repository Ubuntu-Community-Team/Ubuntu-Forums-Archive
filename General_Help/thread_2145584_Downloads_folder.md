---
title: "Downloads folder?"
date: 2013-05-15
forum: General Help
---

### Post by ftkatyowser on 2013-05-15
I'm a newbie to linux, I can get around for the most part but i need to google and research a lot of things.

I had a dual-boot drive where i had installed ubuntu using wubi (ubi?).  Windows crashed and I was able to still boot into ubuntu, where I downloaded the win. 7 iso disk so I could burn it and re-install windows.  well, ubuntu stopped working as well, so I hooked an external hard drive up that boots xubuntu, which is what i'm working out of.  I can navigate the folders and such for the main hard drive, but where are the downloads from the ubuntu os?  they have to be on there somewhere, right?

---

### Post by moody_mark on 2013-05-16
Sounds to me like when you re-installed windows it probably overwrote the MBR and that's why you couldn't boot Ubuntu afterwards. If you can mount the drive when booted from your Xubuntu external disc then you'll likely see two drives, one will be the windows partition and one the old Ubuntu one. Usually they will auto-mount under the /media directory. To Auto-mount just opening up the drive in the file manager should usually do this.

Once you are in /media/<usually some random string>/ then you need to go to home/<user>/Downloads

Hope this helps.

---

