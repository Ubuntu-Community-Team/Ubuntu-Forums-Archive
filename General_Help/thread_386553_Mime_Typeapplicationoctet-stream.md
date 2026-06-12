---
title: "Mime Type/application/octet-stream"
date: 2007-03-17
forum: General Help
---

### Post by reb68 on 2007-03-17
I had the error window continually pop up in Edgy. I upgraded to Fiesty Herd 5 and it is still there. Following is what I get.
---------------------
Sorry
Could not find Mime Type
application/octet-stream
--------------------------------------
Why does this keep popping up. If I try to use "Find/File" it will pop up 40-5- windows like this. I have to ctl-alt-Backspace and reboot to get out of it.

---

### Post by dbbolton on 2007-03-17
when exactly does this error appear ?

---

### Post by n8bounds on 2007-03-28
I had the same problem:

[http://ubuntuforums.org/showthread.php?t=118485&highlight=octet-stream](http://ubuntuforums.org/showthread.php?t=118485&highlight=octet-stream)

A: ```
 rm ~/.kde/share/mimelnk/application/octet-stream.desktop 
```

No reboot/relogon required

---

