---
title: "Brother Printer prints upside on duplex printing"
date: 2019-10-31
forum: General Help
---

### Post by chamois5 on 2019-10-31
I have a Lenova ideapad 320 and a Brother printer, HL-L2315DW running Ubuntu 18.04.  Every other page, back page, prints upside down.  I have tried various tweaks and nothing seems to work.  It's not a big deal on some things, on others it is a pain.  I read somewhere the generic Linux driver Brother uses is the culprit, but it seems to work fine on hubby's HP running Ubuntu.  It prints great otherwise.  Any suggestions are much appreciated in advance.

---

### Post by Skaperen on 2019-10-31
does every page print on a separate sheet?  can this printer print on the back side of sheets directly?  are you trying to print on the back?

---

### Post by SeijiSensei on 2019-11-01
You can install the official Brother driver from its website.  Use the "Driver Install Tool" from [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2315dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2315dw_us&os=128)

---

### Post by kurt18947 on 2019-11-02
> **SeijiSensei said:**
> You can install the official Brother driver from its website.  Use the "Driver Install Tool" from [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2315dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2315dw_us&os=128)

This would get my vote and is what I use. Brother's web site can be a little confusing because they list steps doing a manual install that haven't been needed in Ubuntu in years. The installer script has done what I needed every time I've used it. I also use the app "system-config-printer" to make sure the URI is correct (I have all my devices networked and the installer can default to USB). Make sure the printer is enabled, shared etc. etc.

---

