---
title: "Asus K52JB laptop web camera shows upside-down picture in Skype on Ubuntu 14.04 LTS"
date: 2014-08-25
forum: General Help
---

### Post by s-terenzi on 2014-08-25
As by title, I'm dealing with this annoying problem. I tried already some suggestions like:

```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so  skypeERROR: ld.so: object  '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot  be preloaded (wrong ELF class: ELFCLASS64): ignored.
```

but as you can see i get that error.

Libraries are located as above tried:

```
locate v4l1compat.so
/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so
```

Now don't really know what else to try.
Cheese webcam is working correctly and so the rest.

On another post [http://linuxg.net/how-to-install-skype-4-3-on-ubuntu-linux-mint-pinguy-os-elementary-os-lxle-and-other-ubuntu-derivative-systems/http://](http://linuxg.net/how-to-install-skype-4-3-on-ubuntu-linux-mint-pinguy-os-elementary-os-lxle-and-other-ubuntu-derivative-systems/http://) the guy says that as Skype is made for 32bit, it may need 32 bit libraries so he suggests to install them with sudo dpkg --add-architecture i386, but at the end while updating not sure everything went ok.

Anyone can help please?

Thanks

---

