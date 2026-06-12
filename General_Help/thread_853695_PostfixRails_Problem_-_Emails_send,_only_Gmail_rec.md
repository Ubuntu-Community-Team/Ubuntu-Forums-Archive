---
title: "Postfix/Rails Problem - Emails send, only Gmail recieves"
date: 2008-07-08
forum: General Help
---

### Post by ralphthemagician on 2008-07-08
Problem: Using Postfix to send mail, only Gmail (and Google Apps hosted email) can receive. Yahoo, Hotmail, and pretty much every other email server seem to not receive the email at all.

Background: We have a Rails application using Postfix to send emails for new user registrations. We only tested with Gmail, but now that we are trying to get someone to sign up, they aren't even receiving the email that lets them confirm their email address! It's just bizarre, because Gmail receives these emails just fine. When sent to a Yahoo address though, they don't go to spam, bounce, or anything. It's just as if it was never sent.

Here is the header to the email as seen through Gmail:

```
Delivered-To: gn3nt4@gmail.com
Received: by 10.210.68.12 with SMTP id q12cs663eba;
        Tue, 8 Jul 2008 16:47:14 -0700 (PDT)
Received: by 10.151.102.8 with SMTP id e8mr11290664ybm.61.1215560833558;
        Tue, 08 Jul 2008 16:47:13 -0700 (PDT)
Return-Path: <root@betazone>
Received: from betazone (209-20-69-104.slicehost.net [209.20.69.104])
        by mx.google.com with ESMTP id n63si20407524pyh.8.2008.07.08.16.47.11;
        Tue, 08 Jul 2008 16:47:13 -0700 (PDT)
Received-SPF: neutral (google.com: 209.20.69.104 is neither permitted nor denied by best guess record for domain of root@betazone) client-ip=209.20.69.104;
Authentication-Results: mx.google.com; spf=neutral (google.com: 209.20.69.104 is neither permitted nor denied by best guess record for domain of root@betazone) smtp.mail=root@betazone
Received: by betazone (Postfix, from userid 0)
	id A4628182D6; Tue,  8 Jul 2008 23:47:11 +0000 (UTC)
From: Anatomy Ads Membership <new-user-confirmation@anatomyads.com>
To: gn3nt4@gmail.com
Subject: New User Confirmation
Mime-Version: 1.0
Content-Type: text/html; charset=utf-8
Message-Id: <20080708234711.A4628182D6@betazone>
Date: Tue,  8 Jul 2008 23:47:11 +0000 (UTC)

```

I believe the problem lies in the "Return-Path." How did this get set, and how do we fix it?

-Aaron

---

