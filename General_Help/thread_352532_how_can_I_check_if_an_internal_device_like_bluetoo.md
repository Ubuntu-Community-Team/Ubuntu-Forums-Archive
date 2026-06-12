---
title: "how can I check if an internal device like bluetooth is installed on my system?"
date: 2007-02-03
forum: General Help
---

### Post by Isoss on 2007-02-03
I know by using lspci I can browse all the devices that are installed on my system. I have a laptop with an internal bluetooth device, but I am not sure whether ubuntu autodetected it or not when I installed it. When I use lspci, bluetooth it's not listed! does lspci list all the devices?
Is there another way to find out whether bluetooth is installed?

Thanks.

---

### Post by DarkN00b on 2007-02-03
Try this:

```
sudo lshw |grep blue
```

You can substitute any other word for "blue" to check for that hw.

---

