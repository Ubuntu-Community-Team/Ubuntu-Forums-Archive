---
title: "Mono, Apache, Kubuntu"
date: 2005-08-02
forum: General Help
---

### Post by The Spook on 2005-08-02
WARNING: I'm a newbie.

I installed Kubuntu on my Dell and configured to dual boot to Windows XP & Kubuntu (which was surprisingly pleasant).  I'm wondering how I might be able to run ASP.NET pages on Apache.  I was able to get Apache2 and libapache-mod-mono+dependencies installed via kynaptic, but when I try to view /var/www/test.aspx, it displays the code instead of parsing the page.  How do I get (K)ubuntu and mod_mono to work?

---

### Post by David Marrs on 2005-08-08
I didn't think there was a mono-mod available for apache2 in the repositories. When I tried earlier today I had to install apache 1.3 instead. Is it possible you are using apache2 to serve the pages when it's apache1 that mono's plugged in to?

Alternatively, I presume you are typing 'localhost/test.aspx' in your web browser and not '/var/www/test.aspx'? Obviously you won't get very far if you're doing the latter ;)

---

