---
title: "Can't send email (hotmail) with Thunderbird on Ubuntu 17.10 64-bit"
date: 2017-11-03
forum: General Help
---

### Post by thepict on 2017-11-03
Getting an error message:

Sending of the message failed.
An error occurred while sending mail: Outgoing server (SMTP) smtp-mail.outlook.com is unknown. The server may be incorrectly configured. Please verify that your Outgoing server (SMTP) settings are correct and try again.

I know nothing about SMTP etc. Any ideas how to fix my problems will be greatly appreciated. 
btw, I can receive emails and read them ok, just hasn't been sending for last few days - might have been since last OS update.

---

### Post by lesbillbell on 2017-11-05
I have the same problem exactly since the last OS update. The smtp configuration appears to be correct - port 587, normal password, STARTTLS (SSL/TLS does not work either). I tried clearing Thuunderbird cache, and flushing DNS.

---

### Post by lesbillbell on 2017-11-05
Found a solution: [https://ubuntuforums.org/showthread.php?t=2270096](https://ubuntuforums.org/showthread.php?t=2270096) 
This was -
Try disabling IPv6
set 'network.dns.disableIPv6' to 'true'
(Thunderbird: preferences: advanced: config editor) 
and it worked for me.

---

### Post by lisati on 2017-11-05
@lesbillbell: thanks for the suggestion. Seems to be working here too.

---

