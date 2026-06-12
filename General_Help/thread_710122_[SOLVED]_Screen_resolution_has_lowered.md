---
title: "[SOLVED] Screen resolution has lowered"
date: 2008-02-28
forum: General Help
---

### Post by NovaAesa on 2008-02-28
I was messing around with trying to attach an external monitor to my laptop and I've kinda  messed a few things up. I didn't *really* need to attach an external monitor, I just wanted to do it to see what would happen. So this question isn't really about getting the external monitor to work. The real problem is that now my screen resolution is at 640x480 rather than 1440x900. I think I changed some settings in Sys -> Admin -> Sreens & Graphics.

Could someone help me to fix my lowered screen resolution?
Thanks in advance.

---

### Post by Yellow Pasque on 2008-02-28
Do the old:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work, then you'll have to edit your xorg.conf manually, so post it here.

---

### Post by NovaAesa on 2008-02-28
Thank you! That worked perfectly.

---

