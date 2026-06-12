---
title: "Failed to download package files. check your internet connection."
date: 2015-06-21
forum: General Help
---

### Post by Alduins_Khajiit on 2015-06-21
my Ubuntu WILL NOT update whatsoever!!! it ALWAYS errors out as "Failed to download package files. check your internet connection." after loading a bunch of package files, my internet is fine and is working!!! I can browse, download large files, stream videos, on ALL computers INCLUDING the Ubuntu!!! but Ubuntu just WILL NOT update!!! it has been doing this for A MONTH now!!!

Please help me fix

---

### Post by deadflowr on 2015-06-21
Post the output from the terminal of
```
sudo apt-get update
```

---

### Post by lizard2014 on 2015-06-21
If you're using an unsupported version of Ubuntu, you'll see that kind  of message because the repositories for that release are removed from  the main servers.
Also, cross-check your software sources in the Ubuntu software center.

By the way, which version of Ubuntu are you using?

---

