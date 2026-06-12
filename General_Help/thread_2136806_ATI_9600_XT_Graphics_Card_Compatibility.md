---
title: "ATI 9600 XT Graphics Card Compatibility"
date: 2013-04-18
forum: General Help
---

### Post by Graham1 on 2013-04-18
Hi All

Could someone tell me whether the ATI 9600 XT graphics card (AGP, 256mb) is compatible with Ubuntu 12.10 and 13.04? Are there proprietary drivers available via "additional drivers" or drivers available from ATI's website?

I currently have an NVidia FX5200 (AGP, 128mb) but am stuck on 12.04 LTS as this card is not compatible with 12.10 or 13.04. 

:)

---

### Post by QIII on 2013-04-18
Hello!

That card *may* work if you use the open source Radeon driver installed with Ubuntu.  That will be your only choice.

No proprietary ATI driver will work.  That card is in a legacy driver branch that will not work with any X Server version later than late 2008/early 2009.

Best wishes!

---

### Post by Graham1 on 2013-04-18
> **QIII said:**
> Hello!

That card *may* work if you use the open source Radeon driver installed with Ubuntu.  That will be your only choice.

No proprietary ATI driver will work.  That card is in a legacy driver branch that will not work with any X Server version later than late 2008/early 2009.

Best wishes!

Hi QIII

By "open source Radeon driver installed with Ubuntu", do you mean the driver used if I booted from a live 13.04 cd or would I need to enable this option within the live Ubuntu session?

:)

---

### Post by QIII on 2013-04-18
Either in a Live session or as a fresh install, the Radeon driver is used by default.

---

### Post by ajgreeny on 2013-04-18
I do not think that card will run unity very well, if at all, and it will only use the radeon driver that it gets at install time.

I also suspect that any computer with it in will now be fairly old and therefore better served by either Xubuntu or Lubuntu.

---

