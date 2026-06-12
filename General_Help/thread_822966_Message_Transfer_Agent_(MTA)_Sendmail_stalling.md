---
title: "Message Transfer Agent (MTA) Sendmail stalling"
date: 2008-06-08
forum: General Help
---

### Post by Thomas Tolleson on 2008-06-08
Hello!

My cat crashed my laptop running Gutsy Gibbon, and since that happened my startup has had trouble with a delay/stall when the system declares

Message Transfer Agent (MTA) Sendmail Starting

Any advice on how to keep this delay/stall from occurring?

Thanks!

THT

---

### Post by HalPomeranz on 2008-06-08
Are you seeing any error messages in /var/log/mail.log?

Usually when Sendmail hangs it's having trouble with name resolution.  Do you see anything obviously amiss with /etc/hosts and/or /etc/resolv.conf?  Can you resolve host names (e.g., "host www.google.com", etc)?

---

### Post by talikarng on 2008-06-20
If you aren't using sendmail for anything (I use web based email) try uninstalling sendmail-bin.

---

