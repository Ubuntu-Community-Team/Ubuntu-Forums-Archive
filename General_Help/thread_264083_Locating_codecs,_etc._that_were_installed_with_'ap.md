---
title: "Locating codecs, etc. that were installed with 'apt-get install'?"
date: 2006-09-24
forum: General Help
---

### Post by Leiki on 2006-09-24
Hello,

Is there a way to locate the actual of files of codecs, programs, etc. that were installed by using the 'apt-get install' command? Or does it depend on what is being installed?

Thank you.

---

### Post by Dinerty on 2006-09-24
I use locate command:

```
 locate <file> 
```

---

### Post by hanzomon4 on 2006-09-24
Gstreamer codecs ase located in  /usr/lib/gstreamer-0.10/
The win32 codecs are located in  /usr/lib/win32/
Xine codecs are located in  /usr/lib/xine/plugins/1.1.1/

---

### Post by Anonii on 2006-09-24
> **Leiki said:**
> Hello,

Is there a way to locate the actual of files of codecs, programs, etc. that were installed by using the 'apt-get install' command? Or does it depend on what is being installed?

Thank you.
Using the command:
_dpkg -l | grep <codec name you need>_

You can find the exact package name.
Then using the command:
_dpkg -S <package name you found>_
you can find all the files in there.

Did it answer you question, or I misunderstood you?

---

