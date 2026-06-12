---
title: "What do I type to remove nvidia's restricted drivers?"
date: 2008-02-28
forum: General Help
---

### Post by Mr.Johnny on 2008-02-28
I screwed up... :( 

installed nvidia's restricted drivers in my laptop which has a geforce 7300 go, now it hangs when starting the xserver, not even alt+ctrl+f1 will work.

I must boot in recovery mode, but what do I type to remove it (will be doing doing it later at night)? apt-get uninstall (...)-restricted-modules will do?

Thanks

---

### Post by taurus on 2008-02-28
Just reconfigure your X server to use either vn or vesa so you can boot into GUI again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Then, you can remove or disable it in System -> Administration -> Restricted Drivers Manager.

---

### Post by forestpixie on 2008-02-28
vn ? or nv

---

### Post by Mr.Johnny on 2008-02-29
> **forestpixie said:**
> vn ? or nv

What? :lolflag: Sorry, I am unable to translate.

Anyway... I always mess the dpkg-reconfigure xserver-xorg... :( I was doing dpkg-reconfigure xorg-xserver.

I went to xorg.conf and removed all the stuff related to nvidia and it worked... :p

---

### Post by forestpixie on 2008-02-29
> Just reconfigure your X server to use either *vn* or vesa so you can boot into GUI again.
the vn should be nv

---

