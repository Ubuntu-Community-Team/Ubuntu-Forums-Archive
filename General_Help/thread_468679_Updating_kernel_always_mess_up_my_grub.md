---
title: "Updating kernel always mess up my grub"
date: 2007-06-09
forum: General Help
---

### Post by ekb on 2007-06-09
After every kernel update, it rewrites the grub; however, when it wrote a new one, it put in a wrong config to /boot/grub/menu.lst i.e.
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
instead of
(hd0,6)

To fix this, it really takes me no time but it's just annoying that I have to fix it every kernel update. Any idea how to make it get the right config from the beginning?

thank you.

---

### Post by Pelekophori on 2007-06-09
I used to have this problem too.  I can't remember with absolute certainty, but  I think this is how I solved it. 

Look at  /boot/grub/menu.lst.  Under the section starting:

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
```

should be

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=([COLOR="Red"]hd0,0)[/COLOR]
```

Change the highlighted bit to the device you want and it should remain good after every kernel update.

---

### Post by ekb on 2007-06-09
thank you!
Now I have to wait until the next kernel update to see how it goes. :D

---

