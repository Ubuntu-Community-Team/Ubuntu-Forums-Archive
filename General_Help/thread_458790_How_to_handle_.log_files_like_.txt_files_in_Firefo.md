---
title: "How to handle .log files like .txt files in Firefox"
date: 2007-05-30
forum: General Help
---

### Post by mcook2 on 2007-05-30
Problem: 

You are using Firefox to browse "file:///var/log" and subfolders.

You click on a ".log" file in Firefox and it wants to download it as a tar file instead of just showing you the contents of the file as plain text.    

Solution:

Avoiding editing "/etc/mime.types", in your home directory create the file ".mime.types" containing:

```
text/plain	log
```

And restart Firefox.

---

### Post by liberalist on 2007-05-30
That is a good tip, thank you very much.

---

