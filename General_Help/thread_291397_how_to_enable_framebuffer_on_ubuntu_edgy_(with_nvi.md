---
title: "how to enable framebuffer on ubuntu edgy (with nvidia-glx) ?"
date: 2006-11-02
forum: General Help
---

### Post by ProN00b on 2006-11-02
well, yeah, how to enable framebuffer on ubuntu edgy ?
i tried removing the nvidiafb from /etc/modprobe.d/blacklist-framebuffer and then doing a dpkg-reconfigure, but that didn't work, or rather it didn't make the /dev/fb0 device accessible, i also tried disabling splash on boot in grub, but that didn't make it work either.
can anyone tell me how to enable it ? i mean so i can access it over /dev/fb0 and it uses nvidiafb preferably. thanks in advance!

---

