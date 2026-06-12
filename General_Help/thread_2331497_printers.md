---
title: "printers"
date: 2016-07-22
forum: General Help
---

### Post by trav9595 on 2016-07-22
anyone know a black and white toner laser printer that works right out of the box with Ubuntu???? I am looking for one that also takes cheap toner refill..

---

### Post by DuckHook on 2016-07-23
This question is asked on these forums frequently. It is impossible to provide a useful answer to your question because we have no idea what your needs are. Dual sided? Draft mode? Larger than US letter size? Multi-function? WIFI? Direct from USB?

See what I mean?

A better approach is to narrow your question down to a few desired models that you have researched and that fit your needs. Then ask on these forums if anyone has had problems with them.

---

### Post by Linuxisfast on 2016-07-23
As mod above said but you are totally safe with any HP depending on your need and price point. They are supported out of the box on Linux via HPLIP. Totally plug and play with full features.

---

### Post by DuckHook on 2016-07-23
> **Linuxisfast said:**
> As mod above said but you are totally safe with any HP depending on your need and price point. They are supported out of the box on Linux via HPLIP. Totally plug and play with full features.Agreed, but with just one qualification…

…the newer models are sometimes not supported by the *hplip* repository app and one must download the latest hplip version from the hplip site. I bought a M201dw that was not recognized by Trusty (14.04) until I purged the default hplip and installed the latest standalone app, but worked out of the box in Xenial (16.04). Overall, I agree with you and personally buy nothing but HPs for their general ease of installation and good support. However, even HP will sometimes give a complicated experience to new users unaccustomed to installing separate deb files, mostly with very new models on older Ubuntu  versions.

---

### Post by gordintoronto on 2016-07-23
I have had a good experience with Brother printers.

---

### Post by DuckHook on 2016-07-23
> **gordintoronto said:**
> I have had a good experience with Brother printers.I'm glad you've had a good experience but I've had the opposite experience. A balky driver that required fiddling around with an obscure config file in the guts of Linux to add the Brother vendor and device code, a special driver for scanning, all only available from Brother's site with difficult, obsolete & incomplete instructions, and even then, an unreliable printer driver that sometimes refuses to spool, requiring a reboot.

Though I wouldn't outright discourage people from purchasing Brother, their Linux support is desultory at best.

---

### Post by kurt18947 on 2016-07-23
Right out of the box? I have a Samsung monochrome Multi-Function whose printing function works out of the box using Ubuntu's integrated printer app. The scanner needed Samsung's software that is readily available on Samsung's site. HP is well known for being pretty much plug 'n' play especially if the model has been around for several months. Brother is generally pretty easy to get working but I don't know about 'works right out of the box'. Some of the older Brother models have drivers in the Foomatic data base, newer ones do not. Another trick to remember about Brother lasers is that they closely mimic HP lasers and understand PCL6. They may not be feature complete with PCL6 but they should put toner on paper.

---

### Post by SeijiSensei on 2016-07-24
Printers from Brother can also switched to using Postscript.  I had to switch my HL-3170CDW to PS to print envelopes correctly, and it works fine.

Brother provides a "driver install tool" on its site that will determine the correct drivers for your printer model, then download and install them.  If you have a multifunction device with a scanner, the tool will handle that as well.

---

### Post by kurt18947 on 2016-07-24
> **SeijiSensei said:**
> Printers from Brother can also switched to using Postscript. ** I had to switch my HL-3170CDW to PS to print envelopes correctly, and it works fine.**

Brother provides a "driver install tool" on its site that will determine the correct drivers for your printer model, then download and install them.  If you have a multifunction device with a scanner, the tool will handle that as well.

Really? I'll have to try that. My MFC-6490CW is an absolute PITA to try printing envelopes. Note I said *try.* I've never been able to get #10 envelopes to print with proper margins.

---

### Post by SeijiSensei on 2016-07-25
I think that hint came from here: [https://forums.opensuse.org/showthread.php/497130-How-to-print-envelopes-with-Brother-driver-in-LibreOffice](https://forums.opensuse.org/showthread.php/497130-How-to-print-envelopes-with-Brother-driver-in-LibreOffice)

---

