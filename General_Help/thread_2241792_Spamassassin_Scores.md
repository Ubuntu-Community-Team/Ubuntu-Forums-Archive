---
title: "Spamassassin Scores"
date: 2014-08-28
forum: General Help
---

### Post by robert_boutin2 on 2014-08-28
I have an e-mail server with Ubuntu 12.04, Spamassassin, Postfix, and amavisd-new and I am having some troubles with the Spamassassin score reporting.  I think it's an easy fix but I can't find it, hoping someone else may be able to help.

Basically, if I get an e-mail that is clearly spam, I receive something like the following:
+++++++++
[I]Spam detection software, running on the system "mail.boutinserver.com", has
identified this incoming email as possible spam.  The original message
has been attached to this so you can view it (if it isn't spam) or label
similar future email.  If you have any questions, see
the administrator of that system for details.

Content preview:  To Know more information about this.. hurry ! Click here.
  Burial life insurance for the cost of coffee Burial life insurance can now
   be had for less than a cup of coffee. Rates may be as low as 5.50 per month
   depending upon the requested coverage amount & insured. Visit FastQuote.info
   to get instant quotes from licensed agents: [...] 

Content analysis details:   (4.9 points, 4.0 required)

 pts rule name              description
---- ---------------------- --------------------------------------------------
 0.0 HTML_MESSAGE           BODY: HTML included in message
 1.1 MIME_HTML_ONLY         BODY: Message only has text/html MIME parts
 3.8 RDNS_NONE              Delivered to internal network by a host with no rDNS
 0.0 T_REMOTE_IMAGE         Message contains an external image

The original message was not completely plain text...[/I]
+++++++++
The original spam e-mail is included as an attachment.  But note the spam score above is 4.9, with 4.0 required.  It is correctly identifying the mail as spam, but it is not killing it.

Now when I look at the header information from the same e-mail, I get:
+++++++
[I]Return-Path: <insurance@lafree.eu>
X-Original-To: [EMAIL="xxx@yyy.net"]xxx@yyy.net[/EMAIL]
Delivered-To: [EMAIL="xxx@yyy.net"]xxx@yyy.net[/EMAIL]
Received: from localhost (localhost.localdomain [127.0.0.1])
      by mail.boutinserver.com (Postfix) with ESMTP id ADB763C04DE
      for <xxx@yyy.net>; Thu, 28 Aug 2014 09:13:06 -0400 (EDT)
X-Virus-Scanned: Debian amavisd-new at mail.boutinserver.com
X-Spam-Flag: NO
X-Spam-Score: 0.81
X-Spam-Level: 
X-Spam-Status: No, score=0.81 tagged_above=-999 required=3.9
      tests=[BAYES_50=0.8, HTML_MESSAGE=0.001, NO_RELAYS=-0.001,
      T_REMOTE_IMAGE=0.01] autolearn=ham
Received: from mail.boutinserver.com ([127.0.0.1])
      by localhost (mail.boutinserver.com [127.0.0.1]) (amavisd-new, port 10024)
      with ESMTP id WZour9b5WUap for <nwa@boutinfamily.net>;
      Thu, 28 Aug 2014 09:13:04 -0400 (EDT)
Received: by mail.boutinserver.com (Postfix, from userid 5013)
      id AF19A3C05BF; Thu, 28 Aug 2014 09:13:04 -0400 (EDT)
Received: from localhost by mail.boutinserver.com
      with SpamAssassin (version 3.3.2);
      Thu, 28 Aug 2014 09:13:04 -0400
From: Funeral and Burial Insurance <"Funeral andBurialInsurance"@lafree.eu>
To: <xxx@yyy.net>
Subject: Burial life insurance for the cost of coffee
Date: Thu, 28 Aug 2014 09:13:01 -0400
Message-Id: <65D7134X09614706828689WHS4_@hca.lafree.eu>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----------=_53FF2AE0.4F9A6373"
+++++++
[/I]In the header info, notice that X-Spam-Score=0.81.  I know the "required=3.9" was set in ispconfig.  I also know the "4.0 required" up above I set in a Spamassassin config file.  And I know that amavis is actually handling the spam based on the test results shown in the header (the X-Spam-Score).  If X-Spam-Score hits 3.9, X-Spam-Flag sets to "Yes" and the e-mail is killed. But what I can't understand is why I am getting two sets of scores, and why the one I actually want is different than the X-Spam-Score .  The header information for example doesn't include the scores for:

[I]1.1 MIME_HTML_ONLY
 3.8 RDNS_NONE
[/I]
Any suggestions?

---

### Post by Lido on 2014-09-17
In your amavis conf.d what is the value of ```
$sa_kill_level_deflt
```?

I'm not using ispconfig, but I've noticed that I need to alter amavis conf.d files to adjust any spam filtering.

---

### Post by robert_boutin2 on 2014-09-17
Thanks for helping.  Maybe I'm looking in the wrong place but I have a conf.d directory but I don't see a conf.d file.

/etc/amavis/conf.d/

01-debian
15-content_filter_mode
25-amavis_helpers
05-domain_id
15-content_filter_mode~
30-template_localization
05-node_id
20-debian_defaults
40-policy_banks
15-av_scanners
21-ubuntu_defaults
50-user

I see that statement in 20-debian_defaults:

$sa_spam_subject_tag = '***Amavisd 20-debian spam*** ';
$sa_tag_level_deflt  = 2.0;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 2.9; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 4.5; # triggers spam evasive actions
$sa_dsn_cutoff_level = 5.0;   # spam level beyond which a DSN is not sent

I also see the same set of statements in 50-user:

$sa_spam_subject_tag = '***SPAM*** ';
$sa_tag_level_deflt  = 4.0;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 4.0; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 4.0; # triggers spam evasive actions
$sa_dsn_cutoff_level = 100;   # spam level beyond which a DSN is not sent

My ispconfig settings are tag= -999, tag 2= 3, spam kill= 4, subject tag= *** SPAM? ***

I just received an email with the below header, so in this case it is testing against the ispconfig settings:

[TABLE="width: 99%, align: center"]
[TR]
[TD]**X-Virus-Scanned:** Debian amavisd-new at mail.boutinserver.com
**X-Spam-Flag:** YES
**X-Spam-Score:** 3.071
**X-Spam-Level:** ***
**X-Spam-Status:** Yes, score=3.071 tagged_above=-999 required=3
    	tests=[BAYES_00=-0.001, DKIM_SIGNED=0.1, HTML_MESSAGE=0.001,
    	INVALID_MSGID=0.568, MIME_HTML_MOSTLY=0.428, MPART_ALT_DIFF=0.79,
    	RCVD_NUMERIC_HELO=1.164, T_DKIM_INVALID=0.01,
    	T_FSL_HELO_BARE_IP_2=0.01, UNPARSEABLE_RELAY=0.001] autolearn=no[/TD]
[/TR]
[/TABLE]

I'm really stumped...

But I have never received a spam e-mail that placed that tag in the subject line.

---

