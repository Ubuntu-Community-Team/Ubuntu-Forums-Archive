---
title: "can't send attachments with thunderbird"
date: 2007-01-12
forum: General Help
---

### Post by cyberslayer on 2007-01-12
Whenever I try to send a message that has an attachment I get the following Send Message Error:
"Sending of the message failed.

The message could no be sent because connecting to the SMTP server smtp.comcast.net failed.  The server may be unavailiable or is refusing SMTP connactions.  Please verify that your SMTP server setting is correct and try again, or else contact your network administrator."  I can send messages that don't have attachments without any errors so I don't see why it can't even connect to the SMTP server when there is an attachment.  Anyone know how to fix this?

Thanks

---

### Post by dcstar on 2007-01-12
> **cyberslayer said:**
> Whenever I try to send a message that has an attachment I get the following Send Message Error:
"Sending of the message failed.

The message could no be sent because connecting to the SMTP server smtp.comcast.net failed.  The server may be unavailiable or is refusing SMTP connactions.  Please verify that your SMTP server setting is correct and try again, or else contact your network administrator."  I can send messages that don't have attachments without any errors so I don't see why it can't even connect to the SMTP server when there is an attachment.  Anyone know how to fix this?

Thanks

Try changing your MTU settings (set it lower than the default 1500).

Find your network device with:
```
ifconfig
``` and then do:
```
sudo ifconfig eth0 (or whatever your working device is) mtu 1450
```and see if this affects your sending attachments.

Assuming your are using an ADSL link, what optimal setting will depend on your particular connection type, but 1450 would be a conservative setting that may help.

---

### Post by cyberslayer on 2007-01-14
It works now.  Thanks for your help.

---

