---
title: "Sticky Notes"
date: 2007-11-06
forum: General Help
---

### Post by Gorlist on 2007-11-06
Hi, installed 7.10 and just wondering where the sticky notes program has gone which use to allow you to have boxes on the Desktop? and would appear on bootup.

How do I go about install the latest flash for Firefox? yet to figure it out.

Best Regards,

---

### Post by Sn3ipen on 2007-11-06
To install flash:
Go to:
System-->Administration-->Software Sources-->Third-party software-->Add

Type this into the APT line:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Close the Software soutces window and click yes when it asks you to update your source lists or something like that.

Then go to the teminal window and type:
sudo apt-get install flashplugin-nonfree

---

### Post by Gorlist on 2007-11-06
Thanks for quick reply :) working great!

---

