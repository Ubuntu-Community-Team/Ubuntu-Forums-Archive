---
title: "looking for a simple SMTP daemon that just saves email"
date: 2018-05-10
forum: General Help
---

### Post by Skaperen on 2018-05-10
i am looking for a simple SMTP daemon that just saves email in a big directory *instead* of trying to *deliver it* _regardless of hostname and/or username_.  if anything connects and carries out a valid SMTP protocol, the sent email will be stored in a unique file, named by date at time to either microsecond or nanosecond resolution or something like that.

---

### Post by HermanAB on 2018-05-10
Well, any mail server will do that if the outgoing mail is not configured correctly.  Mail will then simply sit in the outgoing queue.

---

### Post by Skaperen on 2018-05-13
such a server might be able to send mail on.

if i can't find one, it looks like i will need to write one.  then i would have full control over what and how these mail files are written.

---

