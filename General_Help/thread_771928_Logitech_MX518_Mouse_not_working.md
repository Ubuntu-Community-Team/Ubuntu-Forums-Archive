---
title: "Logitech MX518 Mouse not working"
date: 2008-04-28
forum: General Help
---

### Post by amunimanghi on 2008-04-28
Hi,

I recently upgraded to 8.04 and my Logitech MX518 stopped working. It doesn't work in any usb port but I do see it when I type in lsusb.
```
Bus 005 Device 010: ID 046d:c0le Logitech, Inc. MX518 Optical Mouse 
```

Any ideas on how to get this fixed? Thanks

---

### Post by amunimanghi on 2008-04-28
I got it working. I just had to comment the line involving 'pointer mouse' in /etc/X11/xorg.conf and restarted X. Hope this helps other people.

---

### Post by cristovaum on 2008-05-12
> **amunimanghi said:**
> I got it working. I just had to comment the line involving 'pointer mouse' in /etc/X11/xorg.conf and restarted X. Hope this helps other people.

Hi, I have the same prob and like you just upgrade to 8.04... but im Portuguese and didn't quite understood your solution.

Wat do you mean "...to comment the line..." You had to wright something in that section?... Please reply and thanks in advance :)

---

