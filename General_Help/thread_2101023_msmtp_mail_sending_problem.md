---
title: "msmtp mail sending problem?"
date: 2013-01-03
forum: General Help
---

### Post by shamsat on 2013-01-03
I configured the msmtp this is the /etc/msmtprc:

> 
account default
host localhost
port 25
from [email]user@example.net[/email]


This is the command i send the mail from command line:
> 
cat <<EOF | msmtp [email]user2@example.net[/email]
>Subject: test 
>This is a test
>EOF

msmtp can send the mail but there is no from header only the subject as you can see in the  webmail inbox:
 > 
From	 	Subject	 	Date	Size
No From         test message 

As well when you open the mail message there is only Subject and no any other headers like To:, From: and Date: as you can see here the message headers:
> 

INBOX Viewing message  1 / 14    Page 1
			 
Subject: 	test message
  	 
	
Reply Reply to all Forward Attach Edit as new ||  Full headers Raw view Print view Thread view


And these are the Full headers:
> 

	 Return-path: 	<user@example.net>
Envelope-to: 	[email]user2@example.net[/email]
Delivery-date: 	Thu, 03 Jan 2013 21:23:10 +0430
Received: 	from localhost ([127.0.0.1]) by example.net with esmtp (Exim 4.80) (envelope-from <user@example.net>) id 1Tqo2U-0001BN-L7 for [email]user2@example.net[/email]; Thu, 03 Jan 2013 21:23:06 +0430
Subject: 	test message
Flags: 	\Seen 	


---

