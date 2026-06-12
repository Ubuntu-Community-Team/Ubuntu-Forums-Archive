---
title: "Some email being rejected"
date: 2020-12-10
forum: General Help
---

### Post by rsteinmetz70112 on 2020-12-10
I have a customer whose email (outlook) claims it cannot contact our email server. The emails are marked expired, however we have gotten email from this company in the past.

Here is the relevant (I think ) part of a bounce message.

12/9/2020 9:57:15 PM - Server at MN2PR13MB4005.namprd13.prod.outlook.com returned '550 5.4.317 Message expired, cannot connect to remote server(451 5.7.3 STARTTLS is required to send mail)'
12/9/2020 9:47:12 PM - Server at steinmetznet.com (50.251.172.148) returned '450 4.4.317 Cannot connect to remote server [Message=451 5.7.3 STARTTLS is required to send mail] [LastAttemptedServerName=steinmetznet.com] [LastAttemptedIP=50.251.172.148:25] [MW2NAM12FT041.eop-nam12.prod.protection.outlook.com](451 5.7.3 STARTTLS is required to send mail)'

---

### Post by SeijiSensei on 2020-12-10
What SMTP server are you using? Postfix? sendmail? I use sendmail exclusively on CentOS and TLS is active by default.

Maybe this will help? [http://manpages.ubuntu.com/manpages/bionic/man1/postfix-tls.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/postfix-tls.1.html)

---

### Post by ActionParsnip on 2020-12-10
SMTP Error 451 = [https://www.knownhost.com/wiki/email/troubleshooting/error-numbers/451](https://www.knownhost.com/wiki/email/troubleshooting/error-numbers/451)

---

### Post by rsteinmetz70112 on 2020-12-10
I'm using a pretty old install of exim4 that has been been kept current and the OS (Ubuntu) upgraded a number of times. It's been rock solid so I never found any reason to replace it. 
I also never enabled TLS for sending or receiving email since it only accepts outgoing mail from our local network. I've been looking into that. I also have a small apache server which has a Let's Encrypt certificate and I found a cookbook to enable TLS using it so I'm going to try that.

---

