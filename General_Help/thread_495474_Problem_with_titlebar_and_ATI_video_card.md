---
title: "Problem with titlebar and ATI video card"
date: 2007-07-08
forum: General Help
---

### Post by batbuntu on 2007-07-08
I have an ATI "3D Rage Pro 215GP" video card and Ubuntu 7.04. Sorry, I can't figure out how to find out the driver version. It's whatever was installed from the ISO image.

The icons in all application window titlebars are mispositioned. For example in Firefox the Firefox icon, which should be aligned with the left edge of the titlebar, is offset  about 2 inches to the right. The minimize/maximize/close buttons are offset about 2 inches left of the right edge.

I searched the forums and used Google but can't find any info about this problem.

Thanks for your help.

---

### Post by sam0t on 2007-07-08
Hello

Iam Ubuntu newbie but lets see if I can clear something up. First of all, I think what installs from the Ubuntu ISO is a general VGA driver so the problem you are describing might be because of that. Your video card sounds bit dated, but here is a good wiki site for installing drivers for ATI hardware. But remember to check if your hardware is supported by the fglrx drivers:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

ok I checked the site for you and it seems your card might not be supported byt the latest fgrx. However I found this drivers which is ment for cards older than Radeon 9200, so you might want to give it a try:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

Hope that helps

---

### Post by invizibility on 2007-07-08
Those ATI drivers wont work on Feisty. These cards have been deprecated and ATI no longer provides support. You are better off using the xorg drivers that ship with Feisty.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by batbuntu on 2007-07-08
Thanks for the responses!

Yes, I'm trying to re-use an old Win '98 system. Other than this anomaly everything else works fine.

---

