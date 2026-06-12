---
title: "Build Thinstation Package"
date: 2007-01-11
forum: General Help
---

### Post by AidanPS on 2007-01-11
Hi,
      not sure if i have posted this in the right place but i am having problems building the Thinstation package.

i have followed the tutorial from the website, downloaded the tar.gz and uncompressed it.

the problem is in the console when i enter "./build" i get the error:

paul@paul-laptop:~/Thinstation-2.2$ ./build
.: 13: Can't open packages/base/etc/thinstation.functions
 
any ideas on this? 
they arent even a packages/base/etc folders? only "boot-images" and "kernel"

Thanks
-Paul

---

### Post by taurus on 2007-01-11
I guess I can google it for the website but too lazy right now so if you can tell me exactly where you've downloaded it, I can have a look to see how you would build it for your machine.

---

### Post by AidanPS on 2007-01-11
I have followed the tutorial on this link:

[http://thinstation.sourceforge.net/wiki/index.php/TSWIKI-Linuxbuild](http://thinstation.sourceforge.net/wiki/index.php/TSWIKI-Linuxbuild)

the downloaded file is:
[http://optusnet.dl.sourceforge.net/sourceforge/thinstation/Thinstation-2.2.tar.gz](http://optusnet.dl.sourceforge.net/sourceforge/thinstation/Thinstation-2.2.tar.gz)

thanks

---

### Post by taurus on 2007-01-11
What's the output when you run this command from a terminal, in Thinstation-2.2 directory?

```
ls -la packages/base/etc/thinstation.functions
```
You also need to edit build.conf for your client harddrive before you run the ./build command.

---

