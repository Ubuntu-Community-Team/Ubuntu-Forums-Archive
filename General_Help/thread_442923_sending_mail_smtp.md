---
title: "sending mail smtp"
date: 2007-05-14
forum: General Help
---

### Post by mikeymouse on 2007-05-14
I cannot send mail using evolution or thunderbird . I can receive mail but cannot send.
 When i try to send it says 'connection to smtp server failed', actually I get the same error message even when not online and try to send email.
 Does anyone know what is required to be able to send email using a dialup connection?
 My configuration of smtp is correct, as i have setup many systems to send email. It is only in Ubuntu that i have this problem..
 Any and all help would be appreciated.
 thanks mikeymouse

---

### Post by kidders on 2007-05-15
Hi there,

Unless you're doing something odd like proxying or blocking outgoing SMTP connections, all you need is the correct SMTP server settings. It's also vaguely possible your problem is DNS-related, but (like my other suggestion), you would know if that were the case.

The first thing to try is a manual SMTP server connection (eg with telnet), to see what happens.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

