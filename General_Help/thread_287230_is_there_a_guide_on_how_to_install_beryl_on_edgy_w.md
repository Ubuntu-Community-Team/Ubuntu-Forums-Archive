---
title: "is there a guide on how to install beryl on edgy with ATI ?"
date: 2006-10-28
forum: General Help
---

### Post by MaximB on 2006-10-28
I mean a guide that works
beryl+edgy+ATI 9800 Pro

thanks.

---

### Post by John.Michael.Kane on 2006-10-28
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
[http://ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://ubuntuforums.org/showpost.php?p=1547638&postcount=7)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)
[http://ubuntuforums.org/showthread.php?t=271123&highlight=beryl+ati](http://ubuntuforums.org/showthread.php?t=271123&highlight=beryl+ati)

---

### Post by Kure on 2006-10-28
> **MAXDDARK said:**
> I mean a guide that works
beryl+edgy+ATI 9800 Pro

thanks.

OK. I may have found the issue. Check with

```

uname -r

```
that you run the correct kernel. The newest (and the only) one in Edgy is **2.6.17-10-generic**. The kernel sometimes doesn't get updated if it is a custom one - by custom I mean kernel manually selected in e.g. Synaptic.

Just install linux-generic, it will automatically selectec any other required dependencies.

I spent 3 hours before I realised this simple thing.

---

### Post by MaximB on 2006-10-29
thanks

---

