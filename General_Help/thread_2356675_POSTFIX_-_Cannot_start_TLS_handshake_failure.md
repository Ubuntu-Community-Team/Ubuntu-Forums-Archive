---
title: "POSTFIX - Cannot start TLS: handshake failure"
date: 2017-03-25
forum: General Help
---

### Post by kinderly on 2017-03-25
Please check my replies within this thread for updated progress.
Cannot start TLS: handshake failure

That is my current error when trying to install POSTFIX for a verfied amazon SES email to send outgoing email such as password requests on my forum.

---

### Post by lisati on 2017-03-25
There's a whole lot of things that can mess with your ability to send out email. Unfortunately, fixing issues with TLS is outside my area of expertise.

---

### Post by kinderly on 2017-03-25
Ah, not a problem! Really hope someone can lend a helping hand here. Would be a big relief.

---

### Post by kinderly on 2017-03-26
Can anyone please help me with this? :(

---

### Post by SeijiSensei on 2017-03-26
Frankly I think you'll get better help at the MyBB forums: [https://www.google.com/search?q=MyBB+SMTP](https://www.google.com/search?q=MyBB+SMTP)

People here can help with Postfix and sendmail, but who knows what SMTP engine is part of MyBB.  This isn't really an Ubuntu issue, but a MyBB one.

---

### Post by kinderly on 2017-03-26
Can someone help setup postfix?

---

### Post by lisati on 2017-03-26
There are several good guides for setting up Postfix with Ubuntu. Disclaimer: It has been a few years since I've done it myself, so I'm not fully up to speed with recent releases.

I'd suggest taking a look here:[LIST]
[*][https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[*][https://help.ubuntu.com/lts/serverguide/postfix.html](https://help.ubuntu.com/lts/serverguide/postfix.html)
[/LIST]

---

### Post by kinderly on 2017-03-27
Basically this is what I want: 
POSTFIX attached to my paid email account which is verified by Amazon SES. This will be used to send Password resets etc

---

### Post by kinderly on 2017-03-27
Mail LOG for postfix:

SSL_connect error to email-smtp.***-***.amazonaws.com[**.***.***]:465: Connection timed out
Cannot start TLS: handshake failure

However, I can connect to: 
openssl s_client -quiet -crlf -connect email-smtp.***-***.amazonaws.com:465

Obviously the ** are there just to block some info.

Any advice please guys??

---

