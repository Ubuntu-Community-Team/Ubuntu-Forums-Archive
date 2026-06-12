---
title: "Setting For Video Driver"
date: 2008-05-02
forum: General Help
---

### Post by tommyhakinen on 2008-05-02
I just installed Hardy and experienced that there is no more Display & Graphics menu(available in Gutsy). I wanted to check what video driver my Hardy is using. Then I went to /etc/X11/xorg.conf to check the driver. yet, it's not shown there. anyone has any suggestion?

Thanks

---

### Post by chewearn on 2008-05-02
There might be better ways, but this is what I could think of.  Run this in terminal:
```
cat /var/log/Xorg.0.log | grep driver
```

For my system, I got a line like this:
```
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
```

---

### Post by tommyhakinen on 2008-05-02
Thank you very much for the quick reply.

---

