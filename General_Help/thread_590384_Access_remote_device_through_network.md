---
title: "Access remote device through network"
date: 2007-10-24
forum: General Help
---

### Post by adt41287 on 2007-10-24
Is there any way that i could access a remote device on another computer at /dev/video0? it is my capture card.  I tried just mounting the remote root filesystem onto my computer at /dvr on my system, and when i go to test if it works using: ```
cat /dvr/dev/video0 > /media/Movies/test.mpg
```

it returns:
```
cat: /dvr/dev/video0: No such device
```

is there any way around this? do i need certain permissions on my remote system?

thanks!

---

