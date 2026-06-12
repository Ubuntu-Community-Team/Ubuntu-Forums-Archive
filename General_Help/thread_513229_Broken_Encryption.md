---
title: "Broken Encryption"
date: 2007-07-30
forum: General Help
---

### Post by paninero on 2007-07-30
Been running encrypted root for about 1.5 years, based on the Edgy Eft howto.  Worked great, never had a problem.

Recently I upgraded some edgy eft packages, say last 3 months worth, and my system broke, hung on boot.

So I started a new install with feisty fawn, on another drive as a test, did the same how to and everything looks ok, did the stuff like changed the URLs for the console map, loaded aes instead of aes_i586 etc., etc.

However I can't boot on the new encrypted root volume, and sort of resembled the same error as on my old install, and just gives an error after loading the boot console "can't get device information.  So I assume there is some kind of missing link for UDEV or that the /dev/sda3 is not being opened properly.

Anyway know of any similar problems?  I really need to get my computer back up, and an alternative is to roll back my old install I guess, if I can figure out was the problem was.

Thanks

---

### Post by paninero on 2007-07-30
SOLVED;

It was this mentioned over in this thread:

[http://ubuntuforums.org/showthread.php?p=3104471#post3104471](http://ubuntuforums.org/showthread.php?p=3104471#post3104471)

I had the same problem, and I fixed it the following way (in fact, I'm just typing this from my shiny new ThinkPad with root, home and swap on an encrypted LVM partition  ):

I copied /usr/share/initramfs-tools/scripts/init-premount/udev to /etc/initramfs-tools/scripts/init-premount and appended the following line at the end:

Code:

/sbin/udevsettle

---

