---
title: "trying to get sorce"
date: 2013-07-04
forum: General Help
---

### Post by mikulator on 2013-07-04
I need to patch source but have a problem getting source using the following command

```
apt-get source linux-source-3.5.0-34-generic
```

but I get this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux-source-3.5.0-04-generic
```

What is wrong?

---

### Post by arpanaut on 2013-07-04
Do you have your source repositories enabled?

---

### Post by mikulator on 2013-07-05
I think I did (see pic + and then an apt-get update), but I am not sure if I need to do more

[IMG]http://i.stack.imgur.com/ipcjB.png[/IMG]

---

### Post by steeldriver on 2013-07-05
Provided you have the deb-src repositories enabled, you should be able to get the source for your currently installed kernel using

```
apt-get source linux-**image**-$(uname -r)
```

If you need to get a particular minor revision that is different from your currently installed version then you may need to use the git repository, I think

[https://wiki.ubuntu.com/Kernel/SourceCode](https://wiki.ubuntu.com/Kernel/SourceCode)

---

### Post by mikulator on 2013-07-05
Super! Thanks!

This was exactly what I needed

---

