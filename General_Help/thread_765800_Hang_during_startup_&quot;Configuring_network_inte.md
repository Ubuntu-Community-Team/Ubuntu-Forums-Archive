---
title: "Hang during startup: &quot;Configuring network interfaces...&quot;"
date: 2008-04-24
forum: General Help
---

### Post by bobp on 2008-04-24
I just upgraded from g to h today, and everything seems to work fine. Except... during startup, it always hangs displaying various startup text, ending with the line:
  * Configuring network interfaces...

I've left it for a while; if it's just slow, it's mind-numbingly slow.

^C does nothing, but hitting Ctrl-Alt-Del causes it to very quickly come up to the login prompt and I can log on and operate (apparently) just fine.

This is on a Lenovo T61p and it had no trouble with 7.10. I'm not sure what details to post, but if anybody is game to try to help, I'd really appreciate it.

Thanks!
Bob

---

### Post by Patsoe on 2008-04-24
Could be that it's waiting for a dhcp server that's not there. Do you use network-manager to connect? Is your /etc/network/interfaces empty?

---

### Post by bobp on 2008-04-24
No, /etc/network/interfaces isn't empty; but it's the same as it used to be. And yes, it was looking for a dhcp server that isn't here at work; but removing that from the file didn't make any difference.

---

