---
title: "gl needed?"
date: 2006-08-07
forum: General Help
---

### Post by Phili on 2006-08-07
Hello,
I'm pretty new to Ubuntu.

I wanted to install the official nvidia linux drivers for my mainboard, but it says that it needs a program called "gl" where do I get it (it's not in "add/remove programs")?

Thanks

---

### Post by hopstah on 2006-08-07
does that error show up when doing a ```
sudo apt-get install nvidia-glx
```?

---

### Post by Phili on 2006-08-08
it showed up while doing
```
sh /.../.../nvidia.run
```

and it´s not a message of the terminal, it´s a message of the window that opens to install the driver

if it was on windows, i´d install directx and the vga driver first, is it the same on linux too?

---

### Post by 3rdalbum on 2006-08-08
```
sudo apt-get install nvidia-glx
```

That should install the nvidia driver, then you can set it up through:

```
sudo dpkg-reconfigure xserver-xorg
```

By the way, if anything says that it needs "GL", it really means that it needs all the packages which have "mesa" in their name.

---

