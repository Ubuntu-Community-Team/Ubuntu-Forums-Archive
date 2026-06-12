---
title: "Wireless Connection"
date: 2008-01-06
forum: General Help
---

### Post by nlonigro on 2008-01-06
I just loaded Ubuntu on my HP Laptop, my eth1 (wireless connection) is not staying active nor will it pick up a wireless signal.. dont know where to download a possible driver either for it.. somebody help?

---

### Post by nlonigro on 2008-01-06
[B]anyone?[B]

---

### Post by stzasnail on 2008-01-06
Well, wireless drivers can be hard to get working. If you have a copy of the Windows drivers you can try NDIS wrapper ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/))

You may be able to find a .deb of it. (I could only find a .deb in the repos)

---

### Post by ugm6hr on 2008-01-06
> **nlonigro said:**
> I just loaded Ubuntu on my HP Laptop, my eth1 (wireless connection) is not staying active nor will it pick up a wireless signal.. dont know where to download a possible driver either for it.. somebody help?

More information would be helpful - the outputs from:
```
lspci
lshw -C network
iwconfig
ifconfig
```

This is very helpful to resolve the problem yourself: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

