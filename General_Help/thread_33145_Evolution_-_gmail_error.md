---
title: "Evolution - gmail error"
date: 2005-05-09
forum: General Help
---

### Post by mjanssen on 2005-05-09
When using Evolution to access my Gmail accountin Fedora Core 3, I did not have a problem, but running Evolution in Ubuntu has caused issues.

I set it up the same:

Receiving options are:
> 
Host: pop.gmail.com:995
Username: [email]mkjanssen@gmail.com[/email]
Use Secure Connection: Always
Auth. Type: Password

Sending Options are:
> 
Host: smtp.gmail.com:487
Server requires authentication: Yes
Use Secure Connection: Always
Authentication: PLAIN

Every time I hit Send/Receive, I get the following message:
> Evolution Warning

SSL Certificate check for pop.gmail.com:

Issuer:            E=server-certs@thawte.com,CN=Thawte Server CA,OU=Certification Services Division,O=Thawte Consulting cc,L=Cape Town,ST=Western Cape,C=ZA
Subject:           CN=pop.gmail.com,O=Google Inc,L=Mountain View,ST=California,C=US
Fingerprint:       f2:be:86:e4:e2:51:76:aa:b6:00:91:7b:97:a4:e6:f3
Signature:         BAD

Do you wish to accept?

Thus, every time I have to hit "OK". Once I do hit OK, the answer holds for as long as Evolution is open (as far as I can tell). Sometimes the message won't pop up and I will sit there waiting.
Also, I have been unable to send an email through my Gmail account.
I'm downloading Thunderbird at the moment to try that, but I would really like to stick with Evolution, as I have all my mail and calendar info deeply entrenched in it.

Is this a difference in the version of Evolution or is there some setting I can tweak to make this stop or is it Gmail's fault?

---

### Post by filosofic on 2005-12-13
I just got the exact same error as you describe.  Have you had any success resolving it or have you had to switch to Thunderbird?

---

### Post by crispingatiesa on 2005-12-13
It happens when U use thunderbird as well

---

### Post by cstudent on 2005-12-13
Your outgoing smtp port is not correct.


From the Gmail settings site:


	
Configuring other mail clients
You can use the following information to configure POP with many mail clients. If you encounter difficulties, we suggest contacting your mail client's customer support department for further instructions.

Incoming Mail (POP3) Server - requires SSL: 	pop.gmail.com
Use SSL: Yes
Port: 995
Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587
Account Name: 	your Gmail username (including '@gmail.com')
Email Address: 	your full Gmail email address (username@gmail.com)
Password: 	your Gmail password

---

### Post by linbetwin on 2005-12-13
It just happened to me in Windows XP now (Outlook Express). It warned me accepting an invalid certificate or something. I chose "No" and I couldn't download the messages. Then I tried again, chose "Yes" and it worked.

---

### Post by cstudent on 2005-12-13
Hmmmm. Interesting. I just vnc'd into my home computer and tried checking my mail with Evolution. Got the error too. Must be something on the Gmail side.

---

### Post by ekravche on 2006-04-17
[QUOTE=cstudent]Your outgoing smtp port is not correct.


From the Gmail settings site:


	
Configuring other mail clients
You can use the following information to configure POP with many mail clients. If you encounter difficulties, we suggest contacting your mail client's customer support department for further instructions.

Incoming Mail (POP3) Server - requires SSL: 	pop.gmail.com
Use SSL: Yes
Port: 995
Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587
Account Name: 	your Gmail username (including '@gmail.com')
Email Address: 	your full Gmail email address (username@gmail.com)
Password: 	your Gmail password[/QUOTE]

interesting way to configure gmail with evolution. Maybe I'll try it someday.

---

