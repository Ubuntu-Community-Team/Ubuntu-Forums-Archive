---
title: "Connection issues (Need help)"
date: 2020-08-31
forum: General Help
---

### Post by hikticrab on 2020-08-31
I have problems with the internet connection, but when I ping any website 

" kevin@kevin:~$ ping <snip> "
it seems alright. However, other google/DDG pages don't open because of the "Internet issue."

---

### Post by dino99 on 2020-08-31
glance at 'journalctl -b' output into a terminal: red line = error, yellow one stands for warning (harmless)

which release/DE are you using ?

---

### Post by TheFu on 2020-08-31
On Sunday, there was a huge internet outage that hit parts of Europe and North America. Some sites, including UbuntuForums were impacted.  Some huge services, like Cloudflare, a content distribution network, were impacted as well.  My service was up, but I couldn't reach many websites for a few hours.  Mostly, they were using cloudflare, but some others were unavailable too, at least for me.

---

### Post by hikticrab on 2020-09-01
Ubuntu 12.04.01

---

### Post by coffeecat on 2020-09-01
> **hikticrab said:**
> Ubuntu 12.04.01

Ubuntu 12.04 went end of life over 3 years ago and has had no patches or security updates since then. If by 12.04.01 you mean 12.04.1, then you are still on the first point release, and missed out on the 12.04.2 point release which happened **over 7 years ago**. In the circumstances perhaps it is just as well you are experiencing an "internet issue". You should not be connected to the internet at all with such an out-of-date, unpatched, and obsolete operating system. In all conscience no one here can help you with internet problems with 12.04.1. You would be well advised to make a fresh installation of a supported release. If you need help with installing a supported version of Ubuntu, you are very welcome to start a new thread for this.

---

### Post by coffeecat on 2020-09-01
I've just noticed that you re-edited your first post. Originally your first post included a URL in your ping line that linked to a commercial site. Another member of forum staff removed that link because it could have been seen as spam - they gave you the benefit of the doubt. I see that you edited it back in again. I have removed it again, and have closed this thread because:

[list=1][*]Since you claim to be running an unsupported version of Ubuntu there is nothing more to be said.
[*]So that you cannot edit the link back in again.[/list]

Any further such posted links *will* be treated as spam.

---

