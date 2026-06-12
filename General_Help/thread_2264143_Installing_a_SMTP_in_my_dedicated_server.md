---
title: "Installing a SMTP in my dedicated server"
date: 2015-02-05
forum: General Help
---

### Post by Artista on 2015-02-05
Hello everyone.


I own a Unbutu 14.04 server which I am using for a minecraft network server and recently I got the interest in also installing a forum and website in it. I am also very new to this matter.
Long story short, I have the forum up and running but I got the problem where the confirmation emails aren't sending. I even check the error:
"Email to [email]xxx@gmail.com[/email] failed: Unable to send mail."


So I googled about the problem and I found out that I need to have my own local smtp working, so I got into the job of finding out what that is. 
I found that I need to set up postfix, dovecot and Squirrelmail in my server.


I followed this guide [http://www.krizna.com/ubuntu/setup-mail-server-ubuntu-14-04/#dovecot](http://www.krizna.com/ubuntu/setup-mail-server-ubuntu-14-04/#dovecot) and now starts my trouble!
When I tried telnet mail.mydomain.org smtp and then enhlo mail.mydomain.org (Step 12 of postfix) I get the following error:


xxxx@xxxx:~# telnet xxx.xxx.org smtp
Trying xx.xxx.xx.xx...
Connected to xxx.xxx.org.
Escape character is '^]'.
ehlo xxx.xxx.org
Connection closed by foreign host.

(Note I am not using mail.domain.org, I am using contact.domain.org)


I then tried to install dovecot, everything went fine except that I can't log at all with my account on outlook, I assume something is blocked?
I appreciate some help because I am googling and searching everywhere about the problem and can't find a fix, I am not sure what I am doing wrong, I followed all the steps!

Thank you very much! :)

---

### Post by newbie-user on 2015-02-05
If you're running your server from home, some ISPs block port 25, so you might not be able to use SMTP unless you set it for a different port. It would also help if you posted some log files so we can see what's going on.

---

### Post by SeijiSensei on 2015-02-05
What do you see in /var/log/mail.log when the telnet connection is dropped?

Read this for details on how Postfix controls access to the SMTP server: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by Artista on 2015-02-05
Thank you for your replies!

@newbie-user:
I am using a KS-4 kimsufi server, how can I set it up from a different port if it's not possible to use default one? And which log files should I show?

@SeijiSensei
on /var/log/mail.log shows this when I tried to use telnet and ehlo:
Feb  5 23:20:45 contact postfix/smtps/smtpd[18102]: connect from ns357128.ip-xx-xxx-xxx.eu[xx.xxx.xxx.xx]
Feb  5 23:20:56 contact postfix/smtps/smtpd[18102]: SSL_accept error from ns357128.ip-xx-xxx-xxx.eu[xx.xxx.xxx.xx]: -1
Feb  5 23:20:56 contact postfix/smtps/smtpd[18102]: warning: TLS library problem: error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown pr$
Feb  5 23:20:56 contact postfix/smtps/smtpd[18102]: lost connection after CONNECT from ns357128.ip-xx-xxx-xxx.eu[xx.xxx.xxx.xx]
Feb  5 23:20:56 contact postfix/smtps/smtpd[18102]: disconnect from ns357128.ip-xx-xxx-xxx.eu[xx.xxx.xxx.xx]

Also could be possible that I have to change to mail.domain.com isntead of contact.domain.com or that doesn't matter?

---

### Post by SeijiSensei on 2015-02-06
You can't use telnet to connect to a server that expects TLS.  Telnet only works if the server accepts plain-text SMTP.  What if you connect using an SSL-aware client like Thunderbird?

---

### Post by newbie-user on 2015-02-06
Telnet doesn't do TLS. You could try telnet-ssl instead. Also, what hostname did you use to create your server certificate, mail or contact?

---

### Post by Artista on 2015-02-07
> **SeijiSensei said:**
> You can't use telnet to connect to a server that expects TLS.  Telnet only works if the server accepts plain-text SMTP.  What if you connect using an SSL-aware client like Thunderbird?
Allright, but the tutorial doesn't explain that. All they say is to use telnet command and a newbie like me is not expected to know it.
I tried thunderbird and outlook.

> **newbie-user said:**
> Telnet doesn't do TLS. You could try telnet-ssl instead. Also, what hostname did you use to create your server certificate, mail or contact?
I did "contact" as hostname.
I don't know how to uset telnet/TLS any guides?

---

### Post by sandyd on 2015-02-07
> **Artista said:**
> Hello everyone.


I own a Unbutu 14.04 server which I am using for a minecraft network server and recently I got the interest in also installing a forum and website in it. I am also very new to this matter.
Long story short, I have the forum up and running but I got the problem where the confirmation emails aren't sending. I even check the error:
"Email to [email]xxx@gmail.com[/email] failed: Unable to send mail."


So I googled about the problem and I found out that I need to have my own local smtp working, so I got into the job of finding out what that is. 
I found that I need to set up postfix, dovecot and Squirrelmail in my server.


I followed this guide [http://www.krizna.com/ubuntu/setup-mail-server-ubuntu-14-04/#dovecot](http://www.krizna.com/ubuntu/setup-mail-server-ubuntu-14-04/#dovecot) and now starts my trouble!
When I tried telnet mail.mydomain.org smtp and then enhlo mail.mydomain.org (Step 12 of postfix) I get the following error:


xxxx@xxxx:~# telnet xxx.xxx.org smtp
Trying xx.xxx.xx.xx...
Connected to xxx.xxx.org.
Escape character is '^]'.
ehlo xxx.xxx.org
Connection closed by foreign host.

(Note I am not using mail.domain.org, I am using contact.domain.org)


I then tried to install dovecot, everything went fine except that I can't log at all with my account on outlook, I assume something is blocked?
I appreciate some help because I am googling and searching everywhere about the problem and can't find a fix, I am not sure what I am doing wrong, I followed all the steps!

Thank you very much! :)

What forum software are you using?
Most should have an option to sending using SMTP

Generally, for better delivery, there are free SMTP services such as [https://mandrill.com/](https://mandrill.com/) . When sending with a SMTP server on a server, there is a higher chance of the email being rejected/marked as spam.

---

