---
title: "I don't see folders &quot;etc, dev, root&quot;..."
date: 2006-12-02
forum: General Help
---

### Post by Infiltraitor on 2006-12-02
I don't see any of those (plus all the rest) in my home folder... after uninstalling kubuntu. Also, I have the Kubuntu splash/loading screen instead of the Ubuntu when I'm going into Ubuntu.

What can I do? I'll provide any other info...

---

### Post by DigitalDuality on 2006-12-02
try viewing hidden files

---

### Post by taurus on 2006-12-02
```
ls -la ~
ls -la /
```

---

### Post by angrykeyboarder on 2006-12-02
> **Infiltraitor said:**
> I don't see any of those (plus all the rest) in my home folder... after uninstalling kubuntu. Also, I have the Kubuntu splash/loading screen instead of the Ubuntu when I'm going into Ubuntu.

What can I do? I'll provide any other info...

In addition to the suggestions you've recieved, a more permanant solution is: ```
$sudo rm /.hidden /media/.hidden
```Depending on updates you may have to repeat the procedure in the future.

Thankfully this "feature" has been removed in Feisty.

---

