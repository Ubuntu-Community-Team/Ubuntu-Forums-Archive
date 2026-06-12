---
title: "sSMTP not honouring revaliases?"
date: 2015-12-27
forum: General Help
---

### Post by Elorian on 2015-12-27
I&#8217;m having an odd problem with sSMTP. The old email address I was sending all the emails to was [EMAIL="firstname@somehost.com"]firstname@somehost.com[/EMAIL] and it worked great. I'm trying to switch it to a new account over at GMX and the email address is [EMAIL="firstname.lastname@gmx.com"]firstname.lastname@gmx.com[/EMAIL]. Now it's no longer working. I did some searching around online but couldn't find a concrete answer. I'm thinking maybe it's a slight misconfiguration on my part and am hoping someone can point it out. Thank you in advance!


ssmtp.conf


#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=firstname.lastname@gmx.com


# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail.gmx.com:587


# Where will the mail seem to come from?
rewriteDomain=somewhere.ddns.net


# The full hostname
hostname=somewhere.ddns.net


# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
# FromLineOverride=YES
AuthUser=firstname.lastname@gmx.com
AuthPass=fake_password
UseTLS=YES
UseSTARTTLS=YES




revaliases


# sSMTP aliases
# 
# Format:    local_account:Outgoing_address:mailhub
#
# Example: root:your_login@your.domain:mailhub.your.domain:[port]
# where :[port] is an optional port number that defaults to 25.
root:firstname.lastname@gmx.com:mail.gmx.com:587
firstname:firstname.lastname@gmx.com:mail.gmx.com:587




/var/log/mail.log


Dec 27 07:00:28 the.server.hostname sSMTP[19698]: Creating SSL connection to host
Dec 27 07:00:29 the.server.hostname sSMTP[19698]: SSL connection using RSA_AES_128_CBC_SHA1
Dec 27 07:00:31 the.server.hostname sSMTP[19698]: Sent mail for [EMAIL="firstname.lastname@gmx.com"]firstname.lastname@gmx.com[/EMAIL] (221 gmx.com Service closing transmission channel) uid=1003 username=firstname outbytes=922


Received Header


Received: from somewhere.ddns.net ([0.0.0.0]) by mail.gmx.com
(mrgmx102) with ESMTPSA (Nemesis) id 0MSHax-1Zirkb2v2R-00TYNC for
<firstname@somewhere.ddns.net>; Wed, 23 Dec 2015 17:32:39 +0100
Received: by somewhere.ddns.net (sSMTP sendmail emulation); Wed, 23 Dec 2015 11:32:02 -0500
From: [EMAIL="firstname.lastname@gmx.com"]firstname.lastname@gmx.com[/EMAIL]
Date: Wed, 23 Dec 2015 11:32:02 -0500
To: firstname
Subject: Cron <firstname@the.server.hostname> /home/firstname/bin/someTask
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/firstname>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=firstname>
Message-ID: <0LhCDT-1aYVxw43mh-00oV3y@mail.gmx.com>
X-Provags-ID: snipped

---

