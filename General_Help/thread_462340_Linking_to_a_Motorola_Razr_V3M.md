---
title: "Linking to a Motorola Razr V3M"
date: 2007-06-02
forum: General Help
---

### Post by jakev383 on 2007-06-02
Has anyone successfully connected a Motorola V3M (I'm on Verizon) with Ubuntu yet? I've tried how-tos (some dating back to Dapper) for moto4lin, bitpim, etc. and cannot seem to get connected to the phone. I'd like to first be able to transfer files, and then move to bluetooth tethering if it's possible.
Anyone?

---

### Post by eholly on 2007-06-12
I'm having the same problems. I've tried bitpim and it did download the phone info but not upload.  Now a update has caused it to fail to start.   I'm going to beat the bushes at their web site.

                          E Holly

---

### Post by princemanjee on 2007-11-30
> **jakev383 said:**
> Has anyone successfully connected a Motorola V3M (I'm on Verizon) with Ubuntu yet? I've tried how-tos (some dating back to Dapper) for moto4lin, bitpim, etc. and cannot seem to get connected to the phone. I'd like to first be able to transfer files, and then move to bluetooth tethering if it's possible.
Anyone?
 Wow still nothing??

---

### Post by white.armor on 2008-01-31
I was able to get it to work, using bitpim 1.0.4 and my wife's V3m, and a mini USB cable from my USB card reader. Easy actually... (after driving myself crazy to get it to work).
Run bitpim as root, and let it complete starting up BEFORE you plug the USB cable into the phone, in bitpim connection settings choose the /dev/ttyACMO (says it is a USB modem). Bitpim connects fine and you can transfer as needed.

---

### Post by owllmann on 2008-01-31
I have a Razr V3C     It is an older model.  I am having trouble connecting using Bluetooth to  retrieve photos.  An ideas?

---

### Post by white.armor on 2008-01-31
Sorry, I have never worked with bluetooth.

---

### Post by daemon3 on 2008-06-11
> **white.armor said:**
> I was able to get it to work, using bitpim 1.0.4 and my wife's V3m, and a mini USB cable from my USB card reader. Easy actually... (after driving myself crazy to get it to work).
Run bitpim as root, and let it complete starting up BEFORE you plug the USB cable into the phone, in bitpim connection settings choose the /dev/ttyACMO (says it is a USB modem). Bitpim connects fine and you can transfer as needed.

](*,)
Interesting.  I followed the tip you showed, but bitpim doesn't list my phone at all (I have your model).  The closest it comes is V3C and V3CM.  I'm getting really frustrated.  Part of the reason why I bought the phone was the music player!

---

