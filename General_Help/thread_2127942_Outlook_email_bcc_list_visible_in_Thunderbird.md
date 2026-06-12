---
title: "Outlook email bcc list visible in Thunderbird"
date: 2013-03-21
forum: General Help
---

### Post by col48 on 2013-03-21
I know this isn't an Ubuntu issue, but I am at a loss where to go for an answer.....

A friend is sending emails to lots of people using Microsoft Outlook and using the bcc facility so as to hide the list of addressees.  Or so she thought.
When I open the email in Thunderbird (running under Ubuntu) I do not see any of the bcc addressees in the normal window.
But if I do View>Message Source in order to see what route around the web the email has taken I can also see the full list of bcc addressees.  This has only been happening in the last 3 weeks or so and as far as the sender is concerned she has not been doing anything different.  [She is a competent but not savvy computer user]

Can anyone shed any light on this?
In particular, is there something she needs to do?  Bear in mind I have never used Outlook myself, so it needs to be put in terms which won't need follow-up questions!!

Here is an extract from the middle of the Source file:  with redaction in {} to preserve privacy

From: {originator email address}
To: {originator email address again}
Subject: {title}
Date: {date and time}
Message-ID: {usual stuff}
MIME-Version: 1.0
Content-Type: multipart/mixed;
	boundary="----=_NextPart_000_0070_01CE2654.EBEB5560"
X-Mailer: Microsoft Office Outlook 12.0
Thread-Index: {alphanumeric string}
Content-Language: en-gb
X-Originating-IP: {IP address in a range which whois tells me is a Microsoft server}
X-FOPE-CRA-SourceIpAddress: {IP address with same first two parts as on prev line}
X-FOPE-CRA-DRYRUN: 1207119;1
X-FOPE-BFA-SENDER: {originator email address}
X-FOPE-BFA-RECEIVER: {first bcc email address}
X-FOPE-BFA-RECEIVER: {second bcc email address}

---

### Post by SeijiSensei on 2013-03-21
Any well-designed SMTP server like sendmail or Postfix never includes any of the Bcc addresses in the message sent to recipients.  They are only used during the SMTP exchanges with the recipient servers.  However all of this is a server-side issue; there is nothing she can do except use another client or a different mail provider.

Is she using Outlook to connect to a Microsoft Exchange server?  An ISP?  Any solution for this depends on the upstream provider.  For Exchange, I found [this discussion](http://support.microsoft.com/kb/2653006).  Since I don't use Windows servers, the terminology is a bit strange, but perhaps it would make sense to an Exchange administrator.  A Google search for "microsoft outlook bcc" brings up a lot of results, but the few I scanned all indicated the recipients should be hidden.

---

### Post by col48 on 2013-03-21
Thanks, Seiji.  As far as I know she's just connecting to an ISP; I don't think the question would mean anything to her - I'm certain somebody else set things up 2 or 3 years ago.

I found this [http://support.microsoft.com/kb/189999#appliesto]("http://support.microsoft.com/kb/189999#appliesto") which paints the same picture.

Looks like there may be nothing she can do directly except complain!  I can't see her changing to another client or provider; it's a matter of not seeing that it's broke so not seeing that it needs fixing!

---

