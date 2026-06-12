---
title: "synaptic won't open in hardy"
date: 2008-05-30
forum: General Help
---

### Post by bouduin on 2008-05-30
HI all,
 Tried to install libdvdcss2 & codecs got error.Fairly new to ubuntu,I'm stuck.

  E: Type '--18:22:06--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: the list of sources could not be read.
Go to the repository dialog to correct the problem
E:_cache-> open ( ) failed, Please report

---

### Post by quelx on 2008-05-30
open a terminal window (**Applications** > **Accessories** > **Terminal**) and redownload the **medibuntu.list** file

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list
```

then move the file over the offending file

```
sudo mv ./hardy.list /etc/apt/sources.list.d/medibuntu.list
```

retry synaptic

---

### Post by bouduin on 2008-05-31
> **quelx said:**
> open a terminal window (**Applications** > **Accessories** > **Terminal**) and redownload the **medibuntu.list** file

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list
```

then move the file over the offending file

```
sudo mv ./hardy.list /etc/apt/sources.list.d/medibuntu.list
```

retry synaptic

Thanks, I got synaptic back.This really saved the day for me.

---

### Post by Nagulan on 2010-01-10
i need to installed skype. sent link or website

---

