---
title: "Evolution can't access POP3 Server"
date: 2014-04-30
forum: General Help
---

### Post by metal_axe on 2014-04-30
Hello,

I have been trying to get Evolution to connect to my server and retrieve email via POP3. I have configured the email server using dovecot-pop3 and exim4. When using the command line, I can successfully send and receive emails to and from my server. 


```
$ telnet smtp.localdomain 25
Trying fd6b:4101:35ce::1...
Trying 192.168.1.1...
Connected to smtp.localdomain.
Escape character is '^]'.
220 server1.localdomain ESMTP Exim 4.71 Thu, 01 May 2014 00:50:08 +1200
EHLO client1.localdomain
250-server1.localdomain Hello client1.localdomain [192.168.1.11]
250-SIZE 52428800
250-PIPELINING
250 HELP
MAIL FROM:mal@localdomain
250 OK
RCPT TO:mal@localdomain
250 Accepted
DATA
354 Enter message, ending with "." on a line by itself
From: mal@localdomain
To: mal@localdomain       
Subject: Hello

Hi there!
.
250 OK id=1WfTyC-0002Ck-DB
QUIT
221 server1.localdomain closing connection
Connection closed by foreign host.
```


Sent fine, and now retrieving:


```
$ telnet pop3.localdomain 110
Trying fd6b:4101:35ce::1...
Trying 192.168.1.1...
Connected to pop3.localdomain.
Escape character is '^]'.
+OK Dovecot ready.
USER mal
+OK
PASS [password]
+OK Logged in.
LIST 
+OK 1 message:

1 489
.
RETR 1
+OK 489 octets
Return-path: <mal@localdomain>
Envelope-to: mal@localdomain
Delivery-date: Thu, 01 May 2014 02:24:57 +1200
Received: from client1.localdomain ([192.168.1.11])
    by server1.localdomain with esmtp (Exim 4.71)
    (envelope-from <mal@localdomain>)
    id 1WfVR4-0002mS-MY
    for mal@localdomain; Thu, 01 May 2014 02:24:57 +1200
Date: Thu, 01 May 2014 02:24:53 +1200
Message-Id: <E1WfVR4-0002mS-MY@server1.localdomain>
From: mal@localdomain
To: mal@localdomain
Subject: Hello

Hi there!
.
QUIT
+OK Logging out.
Connection closed by foreign host.

```

And it is retrieved fine as well. 

My settings for Evolution:

Identity:
-Name:mal@localdomain
-Full Name: Miss A. Laneous
-Email Address mal@localdomain

Receiving Email:
-Server Type: POP
-Server: pop3.localdomain:110
-Username: mal
-Use Secure Connection: No encryption
-Authentication Type: Password

Receiving Options:
-All unchecked (include check for new messages every * minutes, leaves messages on server, delete after * days, and disable support for all POP3 extensions).

Sending Email:
-Server Type: SMTP
-Server: smtp.localdomain:25

Defaults/Security:
-Unchanged from default settings.


The Evolution debug logs don't have any useful information. I've found Evolution doesn't seem to complain when I make the pop server just a scrambed name (I've found other searches on Google that mention Evolution complaining it can't connect to the POP server, but Evolution hasn't been making any similar complaints to me), also it never asks me to input a password (which is required) to retrieve the emails. My exim4 logs show that the mail is being sent and received perfectly fine.

If any more information is required I can try and supply it.

Thanks in advance for any help that can be offered. :)

---

