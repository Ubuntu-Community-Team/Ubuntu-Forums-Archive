---
title: "Wine unables to find libpng12.so.0 under Ubuntu 12.04"
date: 2014-04-07
forum: General Help
---

### Post by gjoli on 2014-04-07
Hi all,

This is a follow up regarding issues that I faced using wine under Ubuntu 12.04, it was described by another user in this thread : [http://ubuntuforums.org/showthread.php?t=1956216](http://ubuntuforums.org/showthread.php?t=1956216)

We were getting tons of message such as :
 	```

err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng12.so.0

```

And a 
```

sudo apt-get install libpng12-0

```

is claiming 
```

libpng12-0 is already the newest version.

```

 



Finally, the workaround is the following :
```

sudo ln -s /lib/i386-linux-gnu/libpng12.so.0 /usr/lib/libpng12.so.0
sudo ln -s /lib/x86_64-linux-gnu/libpng12.so.0 /usr/lib64/libpng12.so.0

```

Cheers !

---

