---
title: "adobe reader not working on 64bit"
date: 2012-12-16
forum: General Help
---

### Post by Heeter on 2012-12-16
Hi all,

I just recently moved from 32bit ubuntu to 64bit ubuntu.

Everything has gone fine, except for Adobe reader.

In 32bit version, it was working well, in 64bit it looks like it installed correctly, but refuses to open at all.

I downloaded the "AdbeRdr9.5.1-1_i486linux_enu.bin" from adobe website, then ran:

```

chmod 755 AdbeRdr9.5.1-1_i486linux_enu.bin
sudo ./AdbeRdr9.5.1-1_i486linux_enu.bin

```

It looks like it installed correctly, it is listed in Dash and I have a shortcut on the desktop too.

Thanks

Heeter

---

### Post by Heeter on 2012-12-16
Update,

Well I guess it is simply because that 64bit version is not available.

So I guess my next question is: how do I uninstall Adobe reader? Also, what is a good PDF viewer?

Thanks

Heeter

---

### Post by Mopar1973Man on 2012-12-16
You might try evince Document viewer.

```
sudo apt-get install evince
```

---

### Post by Heeter on 2012-12-16
Thanks will try that one,

Also, after a while of trying to figure it out, I finally removed Adobe Reader by using this:

```

sudo /opt/Adobe/Reader9/bin/UNINSTALL

```

Thanks

Heeter

---

### Post by aspergerian on 2012-12-16
I'm running Adobe Reader on a 64 bit Acer 1410 with 4g ram. I removed Evince and haven't been disappointed - other than missing Ubuntu 10.04, having tried Unity, then its "classic", then Mint. Finally backed into Xubuntu and wishing it had a more 10.04-like desktop. Adobe Reader worked in all the aforementioned distros.

---

### Post by oldos2er on 2012-12-17
> **Heeter said:**
> Update,

Well I guess it is simply because that 64bit version is not available.

But you should still be able to run it by installing ia32-libs-multiarch.

> **Heeter said:**
> So I guess my next question is: how do I uninstall Adobe reader? Also, what is a good PDF viewer?

I like Okular.

---

### Post by andrew.46 on 2012-12-18
It might sound a bit stone-age but for quickly viewing pdfs Xpdf can often be sufficient. Mind you if you can get 32bit applications running on your 64bit setup (usually not too much of a problem) the closed source Foxit Reader is well worth a look.

---

### Post by colpliscol on 2013-01-22
[QUOTE=oldos2er;12409218]But you should still be able to run it by installing ia32-libs-multiarch.

Thank you.  I installed this with sudo apt-get install ia32-libs-multiarch and it made Adobe Reader work on my 64 bit 12.04 system.

---

