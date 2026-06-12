---
title: "firefox shuts down when opening a recieved e mail from my smtp server"
date: 2008-03-21
forum: General Help
---

### Post by Daveyrow on 2008-03-21
Hi...i´m novice in linux OS, i installed ubuntu 7.10...i did apache, php, mysql server fine...and then i wanted to send the emails from my computer...so i found this guide for some smtp server config:[here]("http://hodza.net/2007/05/04/smtp-server-postfix-sasl2-mysql/") ..ok i did everything without bigger problems...ok i send email...then i opened firefox...go to my privatemailbox...mail recieved ..so mailing works but when i open email...firefox crash down without any bug report or something ( window just disappear)...
---------------------------------------------------------------------
this is the mail code...so you can watch my smtp configuration in it, just say if there are some ugly things: 

```
Received: from <www-data@mirek> for <vladimirpech@mail255.centrum.cz>
Received: from alpha.sanet.cz ([62.77.91.34])
	by mail5.centrum.cz (Centrum Mailer) with ESMTP
	;Thu, 20 Mar 2008 15:54:45 +0100
X-CentrumSpamScore: -09 
X-SpamDetected: 0
X-VirusDetected: 0
X-Virus-Scanner: This message was checked by NOD32 Antivirus system
	NOD32 for Linux Mail Server.
	For more information on NOD32 Antivirus System,
	please, visit our website: http://www.nod32.com/.
X-ZMailerMID: TOyoF8t225b4d3e47e27ab4
Received: by mirek (Postfix, from userid 33)
	id C72C712CBDB; Thu, 20 Mar 2008 15:45:08 +0100 (CET)
To: vladimirpech@centrum.cz
Subject: Traders Password
From: daveyrow@centrum.cz
Reply-To: daveyrow@centrum.cz
X-Mailer: PHP/5.2.3-1ubuntu6
Message-Id: <20080320144508.C72C712CBDB@mirek>
Date: Thu, 20 Mar 2008 15:45:08 +0100 (CET)

Greetings,

Someone from the IP address 10.3.1.128 requested that your password for Traders be sent to you.

Your password is: simcopreper

Thank you

The Traders web team.

http://10.3.1.128bnt


```

---

