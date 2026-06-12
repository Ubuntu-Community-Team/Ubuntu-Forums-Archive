---
title: "Problems with Java Plugin on Kubuntu"
date: 2007-02-03
forum: General Help
---

### Post by saxsux on 2007-02-03
I'm having some trouble with my keyboard in Java, embedded in webpages.
The keyboard will work sporadically, and then just not work at all. It's not a hardware problem - the keyboard will work fine in other applications.

I'm using Kubuntu Edgy, with Firefox 2, Java 5 (from repos).

Also, I can't (un/re)install the plugin because I keep getting the "other package manager running" error message when I load Adept, even though there aren't any others running (I think the Adept Updater froze while updating a while ago, and it hasn't worked properly since).

---

### Post by true_friend on 2007-02-06
try apt-get -f install

---

### Post by phossal on 2007-02-06
You *can* reinstall the plugin. You can get it by either completely upgrading the JRE you run, by downloading 6.0 directly from SUN, for example, or by downloading 5.0 directly from SUN, and replacing the plugin.

It's an interesting problem you're having. I had a similar problem occasionally with my *flash* plugin, until I downloaded it from Adobe.

---

### Post by chalimac on 2007-02-07
It froze because you must accept the agreement manually. You must remove the package and install it from the command line with apt-get. Then you'll be able to interact with the acceptance screen.

Read some apt-get manual. It's easy.

---

