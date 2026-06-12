---
title: "[SOLVED] Evolution timing out on smtp"
date: 2007-10-25
forum: General Help
---

### Post by Zxaos on 2007-10-25
Hi folks.

Since upgrading to gutsy, I've been unable to send mail using evolution - I get server timeouts (Error while performing operation. Could not connect to [myserver]:Connection timed out). 

The settings I have worked in Fesity, and the server is still working (I can send from another computer, and I can telnet to myhost:587. 

Is anyone else having this issue? I've searched around around most other problems similar to this seem to be from over a year ago. Is there some way to see exactly how evolution is failing?

I can receive email fine, just not send. 

Can someone point me in the right direction please?

---

### Post by jfrorie on 2007-10-26
> **Zxaos said:**
> Hi folks.

Since upgrading to gutsy, I've been unable to send mail using evolution - I get server timeouts (Error while performing operation. Could not connect to [myserver]:Connection timed out). 

The settings I have worked in Fesity, and the server is still working (I can send from another computer, and I can telnet to myhost:587. 

Is anyone else having this issue? I've searched around around most other problems similar to this seem to be from over a year ago. Is there some way to see exactly how evolution is failing?

I can receive email fine, just not send. 

Can someone point me in the right direction please?

Any entries in the system log?

---

### Post by Zxaos on 2007-10-26
Ah, my mistake. The same day I installed 7.10, my host disabled relaying. Not an evolution problem at all.

---

