---
title: "[SOLVED] Firefox 3.0 update changed it to English!"
date: 2008-06-10
forum: General Help
---

### Post by nvteighen on 2008-06-10
Hi!
I've updated FF 3.0b5 to the release candidate (RC1) it has been made available in the repos today. It works fine, just that it is running in English and not in Spanish, as it has been until today. There was also a language pack update (both English and Spanish), so maybe the issue could be there instead?

My language support is completely and properly installed at system-level. But Firefox only recognizes English (Add-Ons->Languages).

So, is there anyone having this issue too? In other languages or only Spanish? Of course, it's a minor bug. I just want it fixed to have consistency on my desktop (everything else is in Spanish!).

Thanks!

---

### Post by Pjotr123 on 2008-06-10
Same problem was reported by several people on the Dutch forum. It seems that the translation packages are delivered later on. Try a switch to the main server, then you have them sooner.

---

### Post by Nepherte on 2008-06-10
Very strange. I have Firefox RC1 in my language. Try installing your locale package for Firefox again:
```
sudo apt-get install mozilla-firefox-locale-yourlocalehere
```
To see all the possible locales, search:
```
apt-cache search mozilla-firefox-locale
```

Another possibility, if the locale package is already installed, is to force Firefox to use your locale. Type ```
about:config
``` in your url bar and look for the value "general.useragent.locale". Set it to your locale.

---

### Post by nvteighen on 2008-06-10
Thanks for your input.

It's quite strange, because I either don't have the mozilla-firefox-locale-en-gb package installed (which is the locale Firefox is now using). It seems Firefox doesn't use that packages, but the GNOME ones?

I'll wait a bit. Maybe the get into the server soon. I've read something similar in the catalan forum, but related to beta 5.

---

### Post by Nepherte on 2008-06-10
I suppose it's because the default language is English in Ubuntu. But did you try installing the mozilla-firefox-locale-es-es package? Or forcing it in about:config? That mostly does the trick.

---

### Post by nvteighen on 2008-06-10
Tried both things, both separated and combined. It didn't work.

---

### Post by Nepherte on 2008-06-11
I thought of another way to get the language back..maybe, that is.
Go to this ftp location, assuming your are still using rc1 and choose your language xpi file: [http://ftp.belnet.be/mirror/ftp.mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/](http://ftp.belnet.be/mirror/ftp.mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/) and install it in the addon manager.

---

### Post by nvteighen on 2008-06-11
> **Nepherte said:**
> I thought of another way to get the language back..maybe, that is.
Go to this ftp location, assuming your are still using rc1 and choose your language xpi file: [http://ftp.belnet.be/mirror/ftp.mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/](http://ftp.belnet.be/mirror/ftp.mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/) and install it in the addon manager.
Thanks! That worked.

---

