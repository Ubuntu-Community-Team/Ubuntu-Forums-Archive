---
title: "Twinkle"
date: 2007-10-27
forum: General Help
---

### Post by TryingSA on 2007-10-27
Hi.  I have installed the latest 7.1 version.  I updated the packages but I cannot find Twinkle to install.  What am I doing wrong?

---

### Post by Maestro23 on 2007-10-27
> **TryingSA said:**
> Hi.  I have installed the latest 7.1 version.  I updated the packages but I cannot find Twinkle to install.  What am I doing wrong?

Twinkle is there.  You need to enable your Universe and Multiverse Repositories.  Goto:

System>>Admin>>Software Sources.

Enable then try your search again.

---

### Post by loell on 2007-10-27
strange, i can find twinkle through ```
apt-cache search
```


```
loell@loell-desktop:~$ apt-cache search Twinkle
twinkle - Voice over Internet Protocol (VoIP) SIP Phone

```

---

### Post by TryingSA on 2007-10-27
Thank you very much!  I will try that.

---

