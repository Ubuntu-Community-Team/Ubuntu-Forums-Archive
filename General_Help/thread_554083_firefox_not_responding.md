---
title: "firefox not responding"
date: 2007-09-18
forum: General Help
---

### Post by xGutsAndGloryx on 2007-09-18
My firefox browser will randomly stop responding. It ends up force quiting i believe it is? what can i do to fix this problem?

---

### Post by ajgreeny on 2007-09-18
Perhaps try disabling ipv6 in about:config.  Filter for ipv6 and edit the entry "network dns.disableIPv6" to true.

---

### Post by xGutsAndGloryx on 2007-09-18
how do i disable it?

---

### Post by codejunkie on 2007-09-19
> **xGutsAndGloryx said:**
> how do i disable it?
open firefox in the location bar type ```
about:config
```hit enter
 
then in the Filter pane type ```
network.dns.disableIPv6
``` then double click the entry to change the value from false to true.

also i have noticed lately that websites with excessive amounts of flash content are locking up firefox frequently on my computer it helped installing

 **[COLOR="Red"][FlashBlock]("https://addons.mozilla.org/en-US/firefox/addon/433")[/COLOR]** you can still use flash content you just click on the stuff you want to view.

---

