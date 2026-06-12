---
title: "Running Ubuntu 12.10 and need QT3"
date: 2013-02-05
forum: General Help
---

### Post by Aydos on 2013-02-05
Hello All,

I decided to swap back to Ubuntu at work from Windows.

Some software that I have to sue at work requires QT3.

I cannot find a successful way to get this installed on Ubuntu 12.10.

Anyone have any ideas?

Every time I try to swap to Linux I end up having to go back to Windows and it is frustrating.

I would like to stick it out this time if I can get my software working.

Thanks in advance.

---

### Post by Cheesemill on 2013-02-05
Have you tried...
```
sudo apt-get install libqt4-qt3support
```

---

### Post by tgalati4 on 2013-02-05
I needed qtdmm to read my electrical meter.  It also needs qt3.  I just grabbed the qt3 library that I needed from the 12.04 repository and used dpkg to install:

libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
qtdmm - GUI for digital multimeter

So if you know the exact qt3 libraries, just install them.  They will sit happily next to the qt4 libraries.  I have not used the dummy package suggested by Cheesemill, but that looks like a valid solution as well.

As a side note:  qtdmm is being rewritten/refactored to use Qt4, but it is not finished yet.  It will be called qtdmm2 when it is released.

And yes, the OP has a good point.  Regressions and finding Windows software replacements are serious impediments to linux adoption.  Patience and diligience are required to fix regressions and find suitable replacements.

Unfortunately linux contains neither:

tgalati4@Dell600m-mint14 ~ $ sudo apt-get install patience diligence
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package patience
E: Unable to locate package diligence

---

### Post by Aydos on 2013-02-05
Does 12.04 have QT3 ?

If so I can drop down to that since it is the LTS anyways.

---

### Post by Aydos on 2013-02-05
> **tgalati4 said:**
> I needed qtdmm to read my electrical meter.  It also needs qt3.  I just grabbed the qt3 library that I needed from the 12.04 repository and used dpkg to install:

libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
qtdmm - GUI for digital multimeter

So if you know the exact qt3 libraries, just install them.  They will sit happily next to the qt4 libraries.  I have not used the dummy package suggested by Cheesemill, but that looks like a valid solution as well.

As a side note:  qtdmm is being rewritten/refactored to use Qt4, but it is not finished yet.  It will be called qtdmm2 when it is released.

And yes, the OP has a good point.  Regressions and finding Windows software replacements are serious impediments to linux adoption.  Patience and diligience are required to fix regressions and find suitable replacements.

Unfortunately linux contains neither:

tgalati4@Dell600m-mint14 ~ $ sudo apt-get install patience diligence
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package patience
E: Unable to locate package diligence

What are the steps to do it this way?

Also, do you know if I could just run Ubuntu 12.04 lts and resolve the issue.

---

