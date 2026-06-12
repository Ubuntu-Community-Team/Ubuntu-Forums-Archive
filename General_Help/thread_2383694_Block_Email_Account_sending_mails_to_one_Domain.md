---
title: "Block Email Account sending mails to one Domain"
date: 2018-01-28
forum: General Help
---

### Post by d.b.read on 2018-01-28
Hello,


I hope I'm on the right board for my question.


I'm running Ubuntu 14.04, with Postfix MTA. I have an e-mail account whose user uses it for private affairs, even though he was forbidden to do so. I want to make sure, that he just can't send any mails to one specific domain.


I believe I'm explaining this to complicated. 


[EMAIL="OneAddress@customer.xxx"]OneAddress@customer.xxx[/EMAIL] -> [EMAIL="someEmail@SpecificDomain.XXX"]someEmail@SpecificDomain.XXX[/EMAIL] 


This is what I want to stop.
Is there a way to achieve this, without setting [EMAIL="OneAddress@customer.xxx"]OneAddress@customer.xxx[/EMAIL] on the spamlist of [EMAIL="someEmail@SpecificDomain.XXX"]someEmail@SpecificDomain.XXX[/EMAIL]?

Regards

---

### Post by SeijiSensei on 2018-01-28
Do other users need to send mail to [email]someEmail@SpecificDomain.XXX[/email]?  If you can to block all mail to the address, see the first reply to the question asked here:  [https://serverfault.com/questions/412638/block-outgoing-mail-to-specific-address-using-postfix](https://serverfault.com/questions/412638/block-outgoing-mail-to-specific-address-using-postfix)

This method uses the check_recipient_access map attached to the [smtpd_recipient_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions") ruleset.  I recommend reading [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) if you have not done so already.

I've haven't needed to combine rules in Postfix, so I don't know how you block mail from a specific sender to a specific destination.  My guess is that it is possible, but you'll need to dig around in the Postfix documentation.

---

### Post by linuchsan on 2018-01-28
Worked for me: [https://blog.tinned-software.net/permanently-reject-a-specific-email-sender-address-using-postfix/](https://blog.tinned-software.net/permanently-reject-a-specific-email-sender-address-using-postfix/)

---

### Post by d.b.read on 2018-01-29
> **SeijiSensei said:**
> Do other users need to send mail to [EMAIL="someEmail@SpecificDomain.XXX"]someEmail@SpecificDomain.XXX[/EMAIL]?  If you can to block all mail to the address, see the first reply to the question asked here:  [https://serverfault.com/questions/412638/block-outgoing-mail-to-specific-address-using-postfix](https://serverfault.com/questions/412638/block-outgoing-mail-to-specific-address-using-postfix)

This method uses the check_recipient_access map attached to the [smtpd_recipient_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions") ruleset.  I recommend reading [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) if you have not done so already.

I've haven't needed to combine rules in Postfix, so I don't know how you block mail from a specific sender to a specific destination.  My guess is that it is possible, but you'll need to dig around in the Postfix documentation.

Thanks for the hint. I'll have a look at the postfix.org. 
Only the one mail user should be blocked, all others need to be able to send to the domain.

---

### Post by d.b.read on 2018-01-29
> **linuchsan said:**
> Worked for me: [https://blog.tinned-software.net/permanently-reject-a-specific-email-sender-address-using-postfix/](https://blog.tinned-software.net/permanently-reject-a-specific-email-sender-address-using-postfix/)
Thanks for your answer, but I believe this is to block from my server side one specific email address or even the domain. I need to block one email address to send from my server to one other domain.

---

