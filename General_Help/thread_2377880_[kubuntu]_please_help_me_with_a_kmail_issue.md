---
title: "[kubuntu] please help me with a kmail issue"
date: 2017-11-17
forum: General Help
---

### Post by benji6 on 2017-11-17
Recently, kmail has stopped being able to send email. It receives okay so long as I ```
akonadictl restart
``` periodically. However, sending email returns an error message:

```
Failed to transport message. Your SMTP server does not support PLAIN. Choose a different authentication method. The server responded: 5.7.8 Username and Password not accepted. Learn more at 5.7.8 https://support.google.com/mail/?p=BadCredentials y127sm1545911ywe.81 - gsmtp
```

The link is not really helpful for errors or issues, but I did change my password to see if that would help. I have not found this problem up on the forums, so here you go. Please help if you can.

---

### Post by pissedoffdude on 2017-11-17
Hi,

Looks like other people have experienced this when using gmail as their provider [https://forum.kde.org/viewtopic.php?f=20&t=96118](https://forum.kde.org/viewtopic.php?f=20&t=96118)

I doubt gmail supports other methods like certificates, so it sounds like you probably have 2fa enabled, in which case you should be able to get around this by allowing kmail in you google account settings

---

### Post by benji6 on 2017-11-18
Ok, it looks like what I had to do was update the password twice, once in receiving and once in sending. The link was helpful in pointing my to the right direction. Thank you.

---

