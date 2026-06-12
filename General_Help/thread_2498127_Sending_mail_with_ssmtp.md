---
title: "Sending mail with ssmtp"
date: 2024-05-31
forum: General Help
---

### Post by hakelm on 2024-05-31
I am trying to automate sending some emails from my Ubuntu 22.04 with ssmtp.
I doesn't work, sometimes but not always mails are sent but with a long delay often ssmtp just hangs.
I have a Thunderbird email client on the same machine, sending mails goes like a flash.
My slightly edited ssmtp.conf:

cat /etc/ssmtp/ssmtp.conf
root=myemail
mailhub=send.one.com:465
rewriteDomain=one.com
UseTLS=YES
UseSTARTTLS=YES
hostname=x22
AuthUser=myemail
AuthPass=mypasswd
FromLineOverride=YES

I believe they are essentially the same as my Thunderbird settings.
What can I do?

---

### Post by currentshaft on 2024-06-01
Have you checked for ssmtp logs under /var/log to see any errors or indicators?

---

