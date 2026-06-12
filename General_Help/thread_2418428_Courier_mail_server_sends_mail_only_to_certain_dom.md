---
title: "Courier mail server sends mail only to certain domains"
date: 2019-05-06
forum: General Help
---

### Post by tognaco on 2019-05-06
I have recently installed Courier in Ubuntu 19.04 server and after sending several test emails I have seen that:

[LIST]
[*]I have received the email sent to [email]antonio@phpwebquest.org[/email]
[*]I don't receive the emails sent to [email]antonio@iescavaleri.com[/email] or [email]antonio.temprano@gmail.com[/email]
[/LIST]

I don't have the slightest idea why I can send email to certain domains and not to others. Any advice, please?

---

### Post by SeijiSensei on 2019-05-06
Are all these destinations hosted at the same place? Do you have forward and reverse DNS resolution configured for your server? Do you have SPF records for your domain(s)?

What errors do you see in /var/log/maillog? Is your mail denied by receiving servers? Why?

There are many reasons why one server might reject your mail while another accepts it.  Most of the time it comes down to the array of armor used to defend against spam.

---

### Post by tognaco on 2019-05-06
Well, I can see that I am not very knowledgeable about this subject. About the first questions, I don't know, I will look into it and try to set the SPF records for my domain. With regards to the errors I get, i don't actually get any. I /var/log/mail.err there are only errors related to postfix, that I had before installing Courier. No errors from Courier.

I'll try to find out the answer to your questions and come back.

---

### Post by SeijiSensei on 2019-05-07
I've never used Courier, but I'm sure it must log every transaction somewhere. 

I'd start with aligning forward and reverse DNS.

---

### Post by HermanAB on 2019-05-07
To add to your mail configuration woes, was your IP address ever in the distant past used to send spam and got listed by any of a million different block lists?  

Try checking your IP addy at Spamhaus: [https://www.dnsbl.info](https://www.dnsbl.info)

---

### Post by SeijiSensei on 2019-05-07
[www.mxtoolbox.com](www.mxtoolbox.com) has a variety of useful diagnostics as well.

---

### Post by tognaco on 2019-05-08
Thank you very much for your advice. I checked my domain and unfortunately it is included in 4 different black lists. Apparently, it's due to the fact that it points to a IP included in a range of IP's from where a lot of spam has been sent. The lists owners don't seem to very very sympathetic either and they says that I shouldn't even bother to ask to be taken out of those lists. So, I think I'm going to have to give up. Thanks anyway.

---

### Post by SeijiSensei on 2019-05-08
Where is the server located? I'd try to secure a different IP address from your provider that isn't on any blacklists. Or maybe your provider has a server of its own you can relay mail through?  I'd raise the issue with them and see what solutions they offer.

---

