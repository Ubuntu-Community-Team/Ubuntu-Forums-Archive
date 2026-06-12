---
title: "Firefox 57.0b1: unity menubar gone?"
date: 2017-09-17
forum: General Help
---

### Post by eezacque on 2017-09-17
I upgraded to Firefox 57.0b1, only to find the global unity menubar is gone; now there is a menubar on top of each window.
Is there a way to get the old situation back, or should I downgrade?

---

### Post by deadflowr on 2017-09-17
from mozilla or from the nightly ppa?

---

### Post by eezacque on 2017-09-17
> **deadflowr said:**
> from mozilla or from the nightly ppa?

From [http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu)

---

### Post by vasa1 on 2017-09-17
Maybe it's from the ppa.

I'm still seeing [https://download.mozilla.org/?product=firefox-](https://download.mozilla.org/?product=firefox-)**_56_**.0b12-SSL&os=linux64&lang=en-US over at [https://www.mozilla.org/en-US/firefox/channel/desktop/](https://www.mozilla.org/en-US/firefox/channel/desktop/) and the nightly from Mozilla, which is what I'm on, is still v57.

---

### Post by deadflowr on 2017-09-17
grab the globalmenu deb for your release from the ppa page:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/pool/main/f/firefox/]("http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/pool/main/f/firefox/")
and install it.

---

### Post by eezacque on 2017-09-17
> **deadflowr said:**
> grab the globalmenu deb for your release from the ppa page:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/pool/main/f/firefox/](http://ppa.launchpad.net/ubuntu-mozilla-daily/firefox-aurora/ubuntu/pool/main/f/firefox/)
and install it.

firefox-globalmenu is already installed

---

### Post by mc4man on 2017-09-17
If it's done thru a 'legacy' extension then kiss it goodbye
[https://www.ghacks.net/2016/11/24/firefox-will-only-support-web-extensions-by-the-end-of-2017/](https://www.ghacks.net/2016/11/24/firefox-will-only-support-web-extensions-by-the-end-of-2017/)

---

### Post by eezacque on 2017-09-17
> **mc4man said:**
> If it's done thru a 'legacy' extension then kiss it goodbye
[https://www.ghacks.net/2016/11/24/firefox-will-only-support-web-extensions-by-the-end-of-2017/](https://www.ghacks.net/2016/11/24/firefox-will-only-support-web-extensions-by-the-end-of-2017/)

Looks like it's time to say goodbye to Firefox...

---

### Post by vasa1 on 2017-09-17
And I think that another extension (ubufox?) also stopped working when Mozilla changed to multi-process. I can't check that because I'm on Firefox 57 direct from Mozilla --- getting prepared for the brave new world ;)

---

### Post by eezacque on 2017-09-21
Looks like this bug was fixed in 57.0~b1+build3-0ubuntu0.16.04.4

---

