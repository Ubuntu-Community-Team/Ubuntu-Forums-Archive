---
title: "Blank Subject &amp; From header when sending email with ssmtp"
date: 2012-12-03
forum: General Help
---

### Post by jjscott on 2012-12-03
[INDENT]I am trying to send an email with ssmtp from my PC and am a bit stumped. I can send it fine from the command line and with a script, but the resulting email varies base how it is sent.
 
From a command line I type the following:
/usr/sbin/ssmtp [EMAIL="me@home.com"]me@home.com[/EMAIL]
To: [EMAIL="recipient1@somewhere.com"]recipient1@somewhere.com[/EMAIL]
From: [EMAIL="me@home.com"]me@home.com[/EMAIL]
Subject: Test email
 
This is the message body
CTRL+D
 
This method works fine. The From name & Subject show up in the recipients email. Basically, it looks like a regular email in the recipients email client just as if I sent it from Outlook.
The "body" of the email only contains "This is the message body" as it should.
 
If I pass a file with the email information to ssmtp on the command line, the email is sent and received, but it comes through with a blank “Subject” and “From” in the header. The only data in the email header is the “To”. The missing Subject & From comes through in the message body of the email. So, when the recipient looks at his/her email client, it looks like it came from no one.
 
For testing purposes I type the following from a command line:
 
/usr/sbin/ssmtp [EMAIL="me@home.com"]me@home.com[/EMAIL] <email.txt
 
Here is the contents of email.txt
 
TO: [EMAIL="recipient1@somewhere.com"]recipient1@somewhere.com[/EMAIL]
FROM: [EMAIL="me@home.com"]me@home.com[/EMAIL]
SUBJECT: Test email
 
This is the message body
 
When the recipient views with email this is what the "body" looks like:
 
From: [EMAIL="me@home.com"]me@home.com[/EMAIL]
Subject: Test email
X-Brightmail-Tracker: AAAAARyBy98=
X-Brightmail-Tracker: AAAAAA==
 
This is the message body
 
 
Any idea what is happening here? 
[/INDENT]

---

