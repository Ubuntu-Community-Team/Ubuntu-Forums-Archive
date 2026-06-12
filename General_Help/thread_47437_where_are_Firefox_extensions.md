---
title: "where are Firefox extensions?"
date: 2005-07-08
forum: General Help
---

### Post by SilvioTO on 2005-07-08
When I clic on tool -> extensions -> download extensions in Firefox I'm redirect on this page: [http://www.mozilla.org/products/firefox/upgrade/?application=%257bec8030f7-c20a-464f-9b0e-13a3a9e97384%257d](http://www.mozilla.org/products/firefox/upgrade/?application=%257bec8030f7-c20a-464f-9b0e-13a3a9e97384%257d)

There are no extensions here... why?  :-|

---

### Post by apollo2011 on 2005-07-08
Well, if you had read the part underneath, about Firefox on Ubuntu, you would have seen, that because of the security updates in 1.04, they do not allow you to install extensions without 1.04.  If you have the latest Firefox from Ubuntu, you have 1.04 but the Ubuntu developers never updated the version from 1.02.  So the Mozilla site won't let you in because it thinks you have still have 1.02.  So there is a workaround.

Type "about:config" into the address bar.

Find the "general.useragent.vendorSub" line and change the value from 1.02 to 1.04.  

Then go to [http://addons.mozilla.org](http://addons.mozilla.org) or go back to Tools, Extensions and follow that link.

---

### Post by Biker on 2005-07-08
This is the first time I see this execellent solution!

Thank you very much.

---

### Post by SilvioTO on 2005-07-09
thanks.

---

### Post by apollo2011 on 2005-07-09
No Problem :)

---

