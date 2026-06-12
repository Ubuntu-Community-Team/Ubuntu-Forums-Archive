---
title: "How do I know if zRAM is useful on my system?"
date: 2013-11-25
forum: General Help
---

### Post by vasa1 on 2013-11-25
```
[10:43 AM] ~ $ dmesg | grep zram
[   23.623097] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   23.633196] zram: Created 2 device(s) ...
[   23.663521] Adding 1002652k swap on /dev/zram0.  Priority:5 extents:1 across:1002652k SSFS
[   23.677369] Adding 1002652k swap on /dev/zram1.  Priority:5 extents:1 across:1002652k SSFS
[11:29 AM] ~ $ 
```

I have a Dell 1545 laptop with Core2Duo and 4 GB RAM running xubuntu-desktop and Openbox on Lubuntu 13.10. Under what conditions will zRAM be useful to me? I don't do any sort of "intensive" CPU- or RAM-hogging stuff.

If I don't need zRAM, is there any merit in turning it off or uninstalling it (if that is possible)? If it's worth doing, how do I turn it off or remove it?

(I have looked at [Using zRAM On Ubuntu 13.04 Linux]("http://www.phoronix.com/scan.php?page=news_item&px=MTM1NjQ"))

---

### Post by sudodus on 2013-11-25
I think you need it if swapping is making your system slow. If you almost never notice it, you will probably not need it.

On the other hand, if zRAM is completely stable and causes no problems, you might as well use it.

---

### Post by vasa1 on 2013-11-25
> **sudodus said:**
> I think you need it if swapping is making your system slow. If you almost never notice it, you will probably not need it.

On the other hand, if zRAM is completely stable and causes no problems, you might as well use it.
Well, I'm not aware that it has caused any problem whatever on my system but I'll run *sudo mv /etc/init/zram-config.conf /etc/init/zram-config.conf.disabled* and see if there's any loss of function.

---

### Post by heir4c on 2013-11-25
zRam is good when you not have much memory like 1GB or less. 
In Lubuntu 14.04 there will use it as default. (What I read about it).
With 4GB you have more than enough memory.

When you use zRam and you type in a terminal:
```
top
```
You will see size of zRam and what he used.

---

### Post by varunendra on 2013-11-25
Isn't zram just a virtual swap? I couldn't decipher it in the output of "top" command. On the other hand, "cat /proc/swaps" gives me a total usage detail which is easy to understand for me. :)

---

### Post by heir4c on 2013-11-25
zram put compressed data in the RAM.
[http://en.wikipedia.org/wiki/Zram](http://en.wikipedia.org/wiki/Zram)

---

