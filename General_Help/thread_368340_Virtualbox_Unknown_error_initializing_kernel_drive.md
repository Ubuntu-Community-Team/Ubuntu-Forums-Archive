---
title: "Virtualbox: Unknown error initializing kernel driver"
date: 2007-02-23
forum: General Help
---

### Post by jollyr0ger on 2007-02-23
hi! 
I've correctly installed virtualbox, also the linux-headers. Then the gui starts. I configure a new vm, but when I start it, it return immediately this error:
```

Unknown error initializing kernel driver (VERR_INVALID_FUNCTION).
VBox status code: -36 (VERR_INVALID_FUNCTION).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

Can someone help me?
Tnx

---

### Post by 434562015 on 2008-05-11
you need the package such as kernel-source   kernel-header

i once missed the same problem!~

---

### Post by inportb on 2008-05-11
Did you install the kernel module? You might want to rebuild it:

```
sudo /etc/init.d/vboxdrv setup
```

---

