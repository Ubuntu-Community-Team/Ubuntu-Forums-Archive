---
title: "Firefox extensions?"
date: 2005-06-08
forum: General Help
---

### Post by Zingam on 2005-06-08
Are there no extensions for the Firefox browser for Linux?

---

### Post by dbloom on 2005-06-08
of course, there are. generally the same extensions, too.

[https://addons.mozilla.org/extensions/?application=firefox/](https://addons.mozilla.org/extensions/?application=firefox/)

---

### Post by Markrian on 2005-06-08
Of course there are! In fact, all extensions (with perhaps one or two exceptions where they use OS functions specifically [if that's even possible]) work on all ports of Firefox. So just go to [http://extensionroom.mozdev.org/](http://extensionroom.mozdev.org/) or wherever you would normally get your extensions and install them, as normal.

If you were trying to get/install extensions via Synaptic, that won't work. There are none in Synaptic. You just install them via the browser.

---

### Post by Zingam on 2005-06-08
[QUOTE=dbloom]of course, there are. generally the same extensions, too.

[https://addons.mozilla.org/extensions/?application=firefox/](https://addons.mozilla.org/extensions/?application=firefox/)[/QUOTE]


Strange... When I try to open this page: I get another page offering me to update my browser, etc.

Instead of the page with the extensions. Firefox opens this one (it redirects):
[http://www.mozilla.org/products/firefox/upgrade/?application=%7bec8030f7-c20a-464f-9b0e-13a3a9e97384%7d](http://www.mozilla.org/products/firefox/upgrade/?application=%7bec8030f7-c20a-464f-9b0e-13a3a9e97384%7d)

I think that when I tried Firefox on Debian I was able to download some extensions but after trying for sometime in Ubuntu, I thought that I might be wrong.

So any idea, why extensions cannot be installed on Firefox in Ubuntu?

---

### Post by oasiscity on 2005-06-08
[QUOTE=Zingam]

So any idea, why extensions cannot be installed on Firefox in Ubuntu?[/QUOTE]

Please follow the instructions mentioned in the comments for the bugreport:
1. input about:config in firefox's address bar, push Enter, then you will see parameters setting for firefox.
2. change the value for the key "general.useragent.vendorSub" to 1.0.4.

---

### Post by Zingam on 2005-06-10
[QUOTE=oasiscity]Please follow the instructions mentioned in the comments for the bugreport:
1. input about:config in firefox's address bar, push Enter, then you will see parameters setting for firefox.
2. change the value for the key "general.useragent.vendorSub" to 1.0.4.[/QUOTE]
 WOW! This is a fix! Thanx!

---

### Post by mike998 on 2005-06-10
Is that fix not there when you go to the extensions page?  When I forgot to change my vendor user agent id, I got two boxes with the bottom one pointing me to the solution to the problem...

---

