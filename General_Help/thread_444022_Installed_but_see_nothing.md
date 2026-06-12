---
title: "Installed but see nothing"
date: 2007-05-15
forum: General Help
---

### Post by au8ust on 2007-05-15
Hi, I just downloaded and installed Wubi using *ubuntustudio-7.04-alternate-i386* via *Wubi-7.04-test2* into c:\

The installing process seems to be fine, then I selected to reboot. _But I didn't see any OS to select on boot._

I checked in C:\ and found boot.ini contains:

```
[operating systems]
c:\grldr="Ubuntu"
[boot loader]
timeout=15

```

So, now the problem is _I can't boot UbuntuStudio_ (I haven't tried Ubuntu yet). Anyone could help?

Thanks in advance!


P.S. Sorry for my English.

---

### Post by ago on 2007-05-15
How comes there is no windows in there?

My bet is that you are booting from a different partition and that bootini is not used. See if you can find a boot.ini in another partition (select to show hidden files) and edit that adding:

c:\grldr="Ubuntu"

---

### Post by au8ust on 2007-05-15
Thanks for the reply :)

I've Windows XP installed to C:\ but I don't know why my boot.ini is located in D:\ which is containing:

```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\grldr="Ubuntu"
```

(The last line is later be added as your advice)

After adding the last line, I restarted the system and see the new menu. So I choose the Ubuntu as it returns an error:

```
Windows could not start because the following file is missing or currupt

<SYSTEMROOT>\SYSTEM32\HAL.DLL

Please re-install a copy of the above file.
```

:(

---

### Post by ago on 2007-05-15
Did you copy grldr and grub.exe to d:\ ?

---

### Post by au8ust on 2007-05-15
> **ago said:**
> Did you copy grldr and grub.exe to d:\ ?

Okay, it seems to be loaded but get error about ```
 /bin/sh: can't access tty; job control turned off
```

:confused:

Edit: I'm using Acer Aspire 5052ANWXMi and I was able to boot normal Ubuntu CD & DVD

---

### Post by ago on 2007-05-15
see if there is any error message above that

---

