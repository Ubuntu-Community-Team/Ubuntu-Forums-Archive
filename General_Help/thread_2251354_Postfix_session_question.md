---
title: "Postfix session question"
date: 2014-11-03
forum: General Help
---

### Post by amish_otaku on 2014-11-03
Short and sweet of it is, 

Why does postfix display the following lines when to my understanding they're referring to the same thing... Here's what I'm talking about

220 SERVERNAMEHERE ESMTP Postfix (Ubuntu)
ehlo SERVERNAMEHERE
250-SERVERNAMEHERE
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN <------THIS 
250-AUTH=PLAIN LOGIN <-----THIS TOO
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
421 4.4.2 SERVERNAMEHERE Error: timeout exceeded

Is there any way to only have AUTH PLAIN LOGIN displayed??

Thanks in advance.

---

### Post by amish_otaku on 2014-11-04
Nevermind... I answered my own question. The second line was a result of the BROKEN SASL AUTHENTICATION within postfix. Thanks for the help...

---

