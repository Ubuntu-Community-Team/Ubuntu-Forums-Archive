---
title: "Freezing issue with one web-site"
date: 2016-11-02
forum: General Help
---

### Post by saigyo-cross on 2016-11-02
Hello, 

I am having an issue with the Guardian news web-site. It if freezing up after a few seconds, requiring a force kill. It is (seemingly) the only web-site affected. 

I am running Chromium in Ubuntu 16:04 LTS. It also is occurring using Firefox. Can anyone assist?

Thank you

Tom

---

### Post by ajgreeny on 2016-11-02
I have just looked at [https://www.theguardian.com/uk-news](https://www.theguardian.com/uk-news) and several sub-pages from there without a problem.

What hardware do you have?

---

### Post by saigyo-cross on 2016-11-02
Hello ajgreeny, 

System 76 Wild Dog Pro, Intel core i5 -6500, GT 730, 64 bit. Do you need any other details? Issue is still happening for me, 2 or 3 seconds then lock down. 

Thank you for any help.

Tom

---

### Post by ajgreeny on 2016-11-03
Graphic card?

---

### Post by saigyo-cross on 2016-11-03
GeForce GT 730/PCIe/SSE2

Thank you.

Tom

---

### Post by dragonfly41 on 2016-11-03
Try disabling browser extensions (if installed)  .. e.g. AdBlock Plus extension has been reported to crash.

---

### Post by ajgreeny on 2016-11-03
> **saigyo-cross said:**
> GeForce GT 730/PCIe/SSE2

Thank you.

Tom
What driver are you using for that; the open source nouveau or a proprietary driver from **Additional Drivers**?
If you're not sure use terminal command ```
lspci -k
``` which will list it, usually close to the top.

---

### Post by saigyo-cross on 2016-11-03
Hello Dragonfly41, 

Yes, I had disabled all extensions.  

The problems seems to have self-resolved! No freezing now. Thank you for the suggestions. Closing the thread. 

Tom

---

### Post by saigyo-cross on 2016-11-03
Thank you ajgreeny, 

The problem has self-resolved. I did nothing but now the web-site seems to be functioning as it should. No freezing for the last hour. Strange. 

Thank you anyway for your suggestions. Good to know that help is nearby. 

Tom

---

