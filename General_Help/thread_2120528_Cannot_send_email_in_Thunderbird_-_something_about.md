---
title: "Cannot send email in Thunderbird - something about Kerberos"
date: 2013-02-26
forum: General Help
---

### Post by scottbomb on 2013-02-26
My school gave me the server settings and it works find with Windows Live Mail but I can't get this to work in Thunderbird on a Xubuntu box. I can get mail and access all the IMAP folders but cannot send email. I keep getting this annoying message:

"Sending of message failed. The Kerberos/GSSAPI ticket was not accepted by the SMTP server. Please make sure you are logged into the Kerberos realm...."

I'm NOT USING KERBEROS. My school specifically said to use "Normal Password" for both IMAP and SMTP. Here are their instructions and my settings: 

IMAP:

Connection Security: SSL/TLD
Authentication Mode: Normal Password
Port: 993

SMTP Server:

Connection Security: STARTTLS
Authentication Mode: Normal Password
Port: 587

In case anyone is familiar with the school, it's Regis University in Denver. Their server name (for both incoming and outgoing) is email.regis.edu.

---

### Post by plucky on 2013-02-27
> Connection Security: STARTTLS
Authentication Mode: Normal Password
Port: 587

Shouldn't that be SSL/TLD

Just a thought

Good Luck

---

### Post by scottbomb on 2013-02-27
I tried it now but still getting the same error. It's as if Thunderbird is trying to use Kerberos/GSSAPI even though I'm not telling it to. The settings I posted above are those given by the school and they work fine in Windows Live Mail but not Thunderbird.

---

### Post by steeldriver on 2013-02-27
Hi

Do you have multiple outgoing (smtp) servers defined (e.g. for a previous non-school account)? if so are you sure that the correct outgoing server is set for the regis account? 

If you don't set the outgoing server explicitly in the 'Account Settings' it chooses the default outgoing server - which may be the wrong one

---

### Post by scottbomb on 2013-02-28
I checked it now. It is attempting to use the same server email.regis.edu with the settings listed above.

---

### Post by steeldriver on 2013-02-28
Are you sure the information you were given is correct? if you try to probe the auth methods by issuing an EHLO it doesn't appear to accept AUTH PLAIN

```

$ telnet email.regis.edu 587
Trying 207.93.211.53...
Connected to email.regis.edu.
Escape character is '^]'.
220 email.regis.edu Microsoft ESMTP MAIL Service ready at Thu, 28 Feb 2013 15:11:23 -0700
[B]EHLO email.regis.edu
[/B]250-email.regis.edu Hello [172.25.1.78]
250-SIZE 20480000
250-PIPELINING
250-DSN
250-ENHANCEDSTATUSCODES
250-STARTTLS
 **250-AUTH GSSAPI NTLM**
250-8BITMIME
250-BINARYMIME
250 CHUNKING
quit
221 2.0.0 Service closing transmission channel
Connection closed by foreign host.

```

This is the equivalent from *my* ISP (which *does* accept normal password)

```

250-STARTTLS
[B]250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
[/B]250-ENHANCEDSTATUSCODES
250 8BITMIME

```

---

