---
title: "Installation of Google Chrome in Ubuntu 10.04 32bit"
date: 2016-08-22
forum: General Help
---

### Post by kyorieryzen on 2016-08-22
Hi Experts,

We are trying to install google chrome on ubuntu 10.04 in our test environment but it seems that 10.04 32bit wasn't supported.
We've searched a lot on google but still no luck to be able to install it. Some have recommended to recompile it the prob is we do not know how to do it.

Please help.

T.I.A

---

### Post by howefield on 2016-08-22
32 bit Chrome is no longer available, also I see you are running a "test" environment but Ubuntu 10.04 is also no longer supported and long since passed end of life.

However given this is a "test" installation if you search for the file name "google-chrome-stable_48.0.2564.116-1_i386.deb" you should find it on mirrors where it is yet to be deleted. Secondly, if you have 32 bit machines with it installed you might still find the deb package in /var/cache/apt/archives and lastly chromium-browser is still available in 32 bit, the software upon which Chrome is built.

---

