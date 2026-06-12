---
title: "file name"
date: 2014-12-21
forum: General Help
---

### Post by sam104 on 2014-12-21
Good day all, 

How do i view the full directory of a device driver filename

---

### Post by bapoumba on 2014-12-21
I'm not quite sure what you are asking for.. Show hidden files ?

---

### Post by TheFu on 2014-12-21
Sorry - I don't understand the question. What is "a device driver filename?"

Devices are in /dev/ (usually).
Drivers are usually under /lib/modules/{kernel}-something .... and depend on the exact chips used inside the device.  On my netbook, there over 3900 driver files, though most are not used.

If you can clarify, then we can clarify back.

Oh - **ls -al** is the way to get a full directory listing, but I don't think that is really your question, but I could be wrong.

---

### Post by tgalati4 on 2014-12-21
Linux uses modules to activate and communicate with hardware.

To display the modules that are currently loaded in your system:

```
lsmod
```

If I want to find out where the module "i915" is located:  (Intel Graphics module for i915 and similar chipsets)

```
locate i915
```

If I want the version of the module and any switches that the module uses:

```
modinfo i915
```

---

### Post by sam104 on 2014-12-22
Thanks for the replies guys, what i am looking for specifically in windows using a utility called driverview i can see the location of my network adapter driver location like this -> C:\Windows\System32\Drivers\Rt86win7.sys

---

### Post by yancek on 2014-12-22
In a terminal, run the following commands consecutively and watch the output:  lshw, lsmod
An explanation at the link below


[http://ubuntuforums.org/showthread.php?t=933054](http://ubuntuforums.org/showthread.php?t=933054)

---

