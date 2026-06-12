---
title: "thunderbird sending problem"
date: 2006-11-12
forum: General Help
---

### Post by jeffg21 on 2006-11-12
I have recently got my thunderbird working again or almost. (thread = thunderbird problem). I am now able to receive my emails but when I try to send I get the following message "An error occurred while sending mail. The mail server responded 5.1.3 <jeff@(none)...Hostname required. Please verify that your email address is correct in your Mail preferences and try again."
I know that it must be quite simple but when I mess around with the preferences and connection settings I still don't get it working. Can someone tell me how to do it.

---

### Post by yabbadabbadont on 2006-11-12
Do you have a firewall enabled?  If so, try opening port 113 (tcp ident service).  Some mail servers require this for authentication.  If it doesn't help, be sure to close the port again.

Here are some details: [https://www.grc.com/port_113.htm](https://www.grc.com/port_113.htm)

---

