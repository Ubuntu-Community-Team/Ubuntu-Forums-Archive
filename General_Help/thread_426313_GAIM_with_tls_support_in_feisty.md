---
title: "GAIM with tls support in feisty"
date: 2007-04-28
forum: General Help
---

### Post by harishg on 2007-04-28
I do not see tls option when I want to access my gmail account in GAIM. Do I need to recompile GAIM to get tls support as i have read that tls is not enabled by default.

---

### Post by lw5 on 2007-04-28
Did you look in the GAIM (Pidgin) [_FAQ section_](http://www.pidgin.im/faq.php#q7)?

Is this what you're looking for?

> 
You will notice GnuTLS will not be included by default, even if the necessary includes and libraries are available; to add SSL support, open the configure script in your favourite editor and replace all instances of "-lnsl" by "-lnsl -lgnutls". Ask no questions :-) it Just Works.


---

