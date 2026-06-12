---
title: "GRUB not booting 8.04 on SATA hdd"
date: 2008-05-19
forum: General Help
---

### Post by nalbion on 2008-05-19
I'm trying to set up a Mythbuntu system with a single SATA hdd, but after installing and rebooting it gets stuck at "GRUB Loading stage1.5."

It works when I install Mythbuntu and GRUB onto a parallel ATA hdd, but as soon as I enable SATA in the BIOS with the SATA drive connected it hangs at 1.5. I've installed Mythbunto onto the SATA using just about every possible combination of install/setup options.  I know it's not (100%) a hardware problem (although I suspect buying a new mobo may solve the problem) because the system boots fine with LILO.  I'm not sure if it's:

a) Mythbuntu making some incorrect assumptions about my configuration and telling GRUB to do the wrong things ("/boot" or "/" being described incorrectly to GRUB).
b) The BIOS not supporting SATA correctly - There's an option in the BIOS "enable onboard SATA", but IRCers and some web pages have suggested there should be other settings to indicate the boot priority (not to be confused with boot order). 
or
c) GRUB not doing something correctly.

My motherboard is described here:
[http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US](http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3100&CATEGORY_TYPE=MB&SITE=US)

---

### Post by jklm988 on 2008-05-19
You write very well, support you! [&#38452;&#33550;&#24310;&#38271;](http://www.8681688.com/dx21.htm) [&#38451;&#30207;](http://www.8681688.com/yang.htm) [&#20195;&#23381;](http://www.daiyunbb.cn)[&#32929;&#39592;&#22836;&#22351;&#27515;](http://www.jfjgk.cn)

---

