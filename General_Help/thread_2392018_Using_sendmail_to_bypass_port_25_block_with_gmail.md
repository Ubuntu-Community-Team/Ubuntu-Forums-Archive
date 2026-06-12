---
title: "Using sendmail to bypass port 25 block with gmail"
date: 2018-05-15
forum: General Help
---

### Post by sniper8752 on 2018-05-15
I am trying to send mail out from my server.  My ISP blocks port 25.  I notice that after configuring my sendmail like this: [https://linuxconfig.org/configuring-gmail-as-sendmail-email-relay](https://linuxconfig.org/configuring-gmail-as-sendmail-email-relay) I get this error: Connection timed out with [127.0.0.1].  I made sure to allow outgoing traffic on ports 25 and 587 in my iptables.

---

### Post by SeijiSensei on 2018-05-16
Does the ISP block 587 as well?

Have you tried this?

```
telnet localhost 25
```

What happens? Do you even see a banner from gmail?

---

### Post by sniper8752 on 2018-05-16
I allowed for only the output on port 25 in iptables on my external interface (as I will only ever want/need to send mail, and not receive).  Does sendmail need iptables port 25 to have a rule in the INPUT table as well?
BTW, it fails to connect.

---

### Post by QIII on 2018-05-16
Closed for Staff review.

---

### Post by QIII on 2018-05-18
As this appears to indicate an attempt to circumvent the ISP's choice to block certain ports for their own purposes, the thread will remain closed.

As stated in the [Ubuntu Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules"), we do not support the violation of ToS or EULAs.

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

---

