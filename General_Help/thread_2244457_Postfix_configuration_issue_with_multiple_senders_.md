---
title: "Postfix configuration issue with multiple senders with different domains"
date: 2014-09-16
forum: General Help
---

### Post by Brian_Bozarth on 2014-09-16
I've set up a new Ubuntu server with Lamp + Postfix as the smtp server.   The server will host multiple websites with different domains.

So I created the postfix server with system mail name for the primary domain (ex: smtp.domain1.com) and added a DNS A Host record for smtp.domain1.com.     Emails are going out correctly for [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL].

Now, I've added a new website where it sends email from a contact form with a different domain (ex: [EMAIL="info@domain2.com"]info@domain2.com[/EMAIL]).    Most of the time it works like to my email, but I guess now the client is getting some bounce backs due to the recipient's spam filter on their mail server.    Wondering if it's because [EMAIL="info@domain2.com"]info@domain2.com[/EMAIL] is not the domain of the sending mail server (smtp.domain1.com)

How do I fix this?    I will need to add more websites with a similar sending config (ex: [EMAIL="info@domain3.com"]info@domain3.com[/EMAIL], etc).   

Brian

---

### Post by SeijiSensei on 2014-09-16
One way to improve your chances of having the mail delivered is to add an [SPF record]("http://www.openspf.org/") to the DNS for every domain you are supporting.  I send mail for a number of domains, all of which have 

```
IN  TXT   "v=spf1 a:smtp.domain1.com ~all"
```

in their DNS zone files.  That tells remote SMTP servers that smtp.domain1.com is the valid sender for mail from the domain in which that TXT record appears.

You should also send yourself a message from each domain and look carefully at the complete headers you receive.  The "Return-Path" header specifies the SMTP "envelope sender" that was announced to the remote SMTP server during the initial handshake.  Make sure that forward and reverse DNS resolution works for the domain part of the envelope sender, and that a valid MX record exists for that name as well.  

For instance, suppose the envelope sender is bounces@domain2.com, and the mail is sent from mail.domain1.com.  Make sure both forward and reverse resolution works for mail.domain1.com, and that domain2.com has an MX record that points to mail.domain1.com.  Then make sure you have an SPF record for mail.domain1.com in the DNS for domain2.com.

---

