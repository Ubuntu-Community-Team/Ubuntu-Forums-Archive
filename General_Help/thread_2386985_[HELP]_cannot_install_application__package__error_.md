---
title: "[HELP] cannot install application / package  error &quot;Newbie here&quot;"
date: 2018-03-13
forum: General Help
---

### Post by scylla- on 2018-03-13
Platform: laptop acer emd443 (x64-supported)
OS: Xubuntu 32 Bit (x86)

Problem: cannot install application / package
error:
```
E: The package viber:amd64 needs to be reinstalled, but I can't find an archive for it.
```

what I did before this happen:

1. Download viber (without knowing that its not available for x86 platform)
2. search for a solution:[https://unix.stackexchange.com/questions/118343/run-64-bit-app-on-32-bit-system-ubuntu](https://unix.stackexchange.com/questions/118343/run-64-bit-app-on-32-bit-system-ubuntu)
3. and use this command: 
```
dpkg --add-architecture amd64
```

now I cannot install anything and I don't know how restore it. and there is a red circle with horizontal white line between my wfi and volume applet
please help. thanks

---

### Post by Autodave on 2018-03-13
The red circle is probably not a problem: I have that on several of my machines.

Why did you install a 32 bit system when your PC can support a 64 bit?

Maybe someone else can be of more assistance, but I would start over with a 64 bit system install.

---

### Post by scylla- on 2018-03-13
> **Autodave said:**
> Why did you install a 32 bit system when your PC can support a 64 bit?

Because of my RAM. I only have 2GB, and 64bit is a little bit laggy

---

### Post by kc1di on 2018-03-13
This web page will show you how to restore the original repository source list so you'll be able to update again. [http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html]("http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html")
good luck. 

P.S. there is a link there to create new original source list. [https://repogen.simplylinux.ch]("https://repogen.simplylinux.ch")

---

