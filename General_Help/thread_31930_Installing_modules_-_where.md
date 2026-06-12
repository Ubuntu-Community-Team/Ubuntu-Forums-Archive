---
title: "Installing modules - where?"
date: 2005-05-05
forum: General Help
---

### Post by ghaspias on 2005-05-05
I compiled some modules, but don't know how to install them. Running 'make install' put the *.ko in /lib/modules/2.6.10/extra, but the when I run modprobe the system doesn't find them.

---

### Post by Takis on 2005-05-05
```
insmod my_module.ko
```

---

### Post by ghaspias on 2005-05-05
Well, I'm aware that I can just insmod given the correct path, I have done that and everything is working. But I want the module to be loaded automatically when needed (not necessarily at boot) without having to do insmod.

---

### Post by Takis on 2005-05-05
Okay, try putting it in /etc/modules/2.6.10/misc

(out of curiousity, what prompted you to put it in /etc/modules/2.6.10/extra? Habit from another distro of Linux?)

Also, have you mentioned your mod in /etc/modules?

---

### Post by ghaspias on 2005-05-06
[QUOTE=Takis]Okay, try putting it in /etc/modules/2.6.10/misc

(out of curiousity, what prompted you to put it in /etc/modules/2.6.10/extra? Habit from another distro of Linux?)

Also, have you mentioned your mod in /etc/modules?[/QUOTE]
 Takis:
1- I'll try that.
2- I didn't put it there, the 'make install' did it.
3- No, I didn't add anything manually to /etc/modules. I'll look into it too.
By the way, what I am talking about is a driver for a Zydas ZD1201-based usb Wi-Fi adapter. I also compiled the cdfs module, and have the same problem with that one.

I am not a total newbie in Linux terms, but I have not used Linux for almost two years. Now I'm trying Ubuntu because I want something I can set up quickly, as my HD is having some problems and I might have to re-install soon. Also, I am looking for a Linux distro that I can install to some other people's machines, without incurring in too much trouble configuring and explaining it. So, my current atitude is 'I refuse to act like a geek, I need simple solutions'. Compiling a module, altough it was just a matter of downloading, extracting, and  running 'make', wasn't in my original plan...

---

