---
title: "Spam Assisn errors"
date: 2008-04-03
forum: General Help
---

### Post by mcraul on 2008-04-03
Hi all,

I was wondering anybody encountered this type of error while running spam assisn. While looking at the maillog I found this error repeating over and over


[I]Apr  3 08:23:51 ws096 last message repeated 2 times
Apr  3 08:23:51 ws096 spamd[369]: Number found where operator expected at (eval 1280) line 10, near "} 
Apr  3 08:23:51 ws096 spamd[369]:  
Apr  3 08:23:51 ws096 spamd[369]:  1" 
Apr  3 08:23:51 ws096 spamd[369]:  (Missing operator before  
Apr  3 08:23:51 ws096 spamd[369]:  
Apr  3 08:23:51 ws096 spamd[369]:  1?) 
Apr  3 08:23:51 ws096 spamd[369]: rules: failed to run header tests, skipping some: syntax error at (eval 1280) line 11, near "; 
Apr  3 08:23:51 ws096 spamd[369]: }" 
Apr  3 08:23:51 ws096 spamd[369]: Use of uninitialized value in concatenation (.) or string at /usr/lib/perl5/vendor_perl/5.8.5/Mail/SpamAssassin/PerMsgStatus.pm line 2669, <GEN216166> line 99. 
[/I]

Any Ideas on what could be causing this?

Thanks!

---

