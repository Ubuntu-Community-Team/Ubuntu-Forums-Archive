---
title: "[SOLVED] URLFilter Category"
date: 2008-05-08
forum: General Help
---

### Post by iaculallad on 2008-05-08
This could not be the best forum for posting this query but I'm pushing my luck and hoping someone who used Ubuntu and IPCop had experienced or seen it before.

My IPCop 1.4.18 is running with ADVproxy 2.1.9, URLFilter 1.9.2, and SARG 1.4.16. For the past 1 week that I installed it (I replaced our company's ISA server), company users are getting error messages when browsing sites (mostly on their gmail and yahoo accounts). I tried looking at the error pages on their workstations and it is from the URLFilter's access denied page. On the category on the error page, it just displayed [Files] and nothing else. Webmail was unchecked so I see no other reason why it produces that error message. How could I solve this? What is that [File] category, I can't see it on the URLFilter's setting.

---

### Post by garyedwardjohnston on 2008-05-08
If I were you I'd try one at a time and see if they work.  I'd start with API's.

Good luck!

---

### Post by iaculallad on 2008-05-08
API's as in Application Programmers Interface? How will I do that here in my IPCop machine?

---

### Post by garyedwardjohnston on 2008-05-08
Just try turning off one at a time to find the culprit.

How many filters can there be?

---

### Post by iaculallad on 2008-05-08
I just got four filters activated on IPCop, namely: Proxy, JobSearch, Dating, and Spyware. All other categories are uncheck and allowed google/yahoo domain on the whitelist. What else could I be missing?

Is .google.com / .yahoo.com the right way of enabling the whole of google.com/yahoo.com?

---

