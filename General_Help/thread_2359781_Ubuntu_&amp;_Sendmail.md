---
title: "Ubuntu &amp; Sendmail"
date: 2017-04-27
forum: General Help
---

### Post by g3kxyz on 2017-04-27
I'm not sure if this is even the properly website to ask this question but I have a Ubuntu server setup at home with a phpbb3 forum on it and a couple other websites.

I setup sendmail so I can get phpbb3 e-mails working so members can get notifications.

The problem comes in that users who are on the Office 365 platform can't receive e-mails from my server using sendmail because Office 365 rejects it on some level.

Here is the error (below as an attachment) I'm seeing and I'm trying to figure out exactly what I need to do so Office 365 will accept the e-mails. I'm assuming maybe I need an SSL Cert but I'm not sure?

[ATTACH=CONFIG]274794[/ATTACH]

---

### Post by TheFu on 2017-04-28
Welcome to the forums.

Static IP or dynamic from your ISP?  Most real email systems reject dynamic IP ranges.
Also, if you aren't an expert at sendmail, most people with normal email needs, even with multiple domains are better off using postfix over sendmail.

Please copy/paste text. Save bandwidth for us low-bandwidth people.

---

### Post by mastablasta on 2017-04-28
looks like Outlook thinks you are spamming the users. 

perhaps the issue is with Office 365 settings and filters?!

---

### Post by HermanAB on 2017-04-28
Forward your mail through your ISP mail server (or gmail) - don't send it direct.

---

### Post by SeijiSensei on 2017-04-28
1) Are you using a domain that you control?  

2) Do you have [SPF]("http://www.openspf.org/") records set up for that domain?

3) Do you have both forward and reverse DNS configured for your server's IP address?

4) If you are on a residential connection, many servers will reject your mail.  You'll need to arrange to relay it through your ISP's server.  Many ISPs forbid servers on their residential connections, so they may not offer a relaying service for you.

5) Check to see whether your IP is blacklisted at [https://mxtoolbox.com/blacklists.aspx](https://mxtoolbox.com/blacklists.aspx).

In a world where well over 90% of email traffic is spam, many servers have pretty stringent rules about permitting inbound mail.

---

