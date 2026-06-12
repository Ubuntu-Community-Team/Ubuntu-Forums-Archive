---
title: "Stop Postfix/amavis reject message from revealing mapped boxes"
date: 2014-11-23
forum: General Help
---

### Post by robsoles on 2014-11-23
If this looks TL and you D want to R the whole thing then the bottom line might be all you need to help me :)

I was annoyed to find out that people sending us .exe files were not being notified that their email did not make it to their intended recipient. I checked all the configuration files and found that in some or other update '21-ubuntu_defaults' for amavis had 'discard' where I would prefer to have reject so I copy/pasted the relevant lines to '50-user' and sent our 'main' address a nice email with an exe attachment.

When I saw the following message I rolled my eyes, # marked out the relevant lines in '50-user' and restarted amavisd-new again.

```


This is the mail system at host mx.other-example.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this pfreddylem report. You can
delete your own text from the attached returned message.

                   The mail system

<gerald@example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)

<gringo@example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)

<george@example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)

<freddy@example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)

<mowgli@example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)

<deadbeef@other-example.com> (expanded from <sales@example.com>): host
    127.0.0.1[127.0.0.1] said: 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe (in reply to end of
    DATA command)



Reporting-MTA: dns; mx.other-example.com
X-Postfix-Queue-ID: 60C9560135
X-Postfix-Sender: rfc822; sales@example.com
Arrival-Date: Mon, 24 Nov 2014 09:25:41 +1100 (AEDT)

Final-Recipient: rfc822; gerald@example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe

Final-Recipient: rfc822; gringo@example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe

Final-Recipient: rfc822; george@example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe

Final-Recipient: rfc822; freddy@example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe

Final-Recipient: rfc822; mowgli@example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe

Final-Recipient: rfc822; deadbeef@other-example.com
Original-Recipient: rfc822;sales@example.com
Action: failed
Status: 5.7.0
Remote-MTA: dns; 127.0.0.1
Diagnostic-Code: smtp; 554 5.7.0 Reject, id=17352-01 - BANNED:
    application/x-ms-dos-executable,.exe,.exe-ms,p7zip.exe



Return-Path: <sales@example.com>
Message-ID: <54725EDC.1060507@example.com>
Date: Mon, 24 Nov 2014 09:25:32 +1100
From: "Example Co. Pty Ltd" <sales@example.com>
Organization: Example Co. Pty Ltd.
MIME-Version: 1.0
To: "Sales at Example Co." <sales@example.com>
Subject: This should be a notified bounce now.
Content-Type: multipart/mixed;
 boundary="------------030702020904020901060407"
```

So, both amavis and postfix are putting their 2-cents in to reveal all the individuals that 'sales@example.com' goes to and to say that is undesirable is rather an under-statement - if a business partner/customer sends an exe we want them told it failed and they don't need all our individual addresses, if it is a scumbag sending it we definitely do not want them to get all our individual addresses...

I've gone through customizing the rejection messages for both amavis and postfix - for amavis I am fairly certain that I can make it stop doing that by making a custom message and not including the variable I see being expanded to the individual recipients but I have placed (and tested) customised messages for postfix and the list of recipients is (quite apparently) added after the customised message with no apparent control provided in the custom message to make it not do that.

I keep going back and forth over pages like [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html) with no luck, I probably manage to keep skipping the relevant section(s) where I have tried really hard not to skip anything.


Finally the question: Does anybody know how to make postfix stop advertising the individuals hiding behind the 'main' mail-box in rejection messages?

---

### Post by lisati on 2014-11-23
It's not a good idea to let amavis do any of the rejecting. Issues relating to the unintentional revealing of aliased email addresses aside, the way you've got things set up you risk being labelled as a [backscatterer]("http://en.wikipedia.org/wiki/Backscatter_%28email%29"). 

I'd recommend doing something similar to the method described here: [http://www.cyberciti.biz/tips/postfix-block-mime-attachment-files.html](http://www.cyberciti.biz/tips/postfix-block-mime-attachment-files.html)

---

### Post by robsoles on 2014-11-23
OK, fair point - having it rejected in the initial 'conversation' with postfix is definitely better, offending 'sender' should be informed without any risk of ever being labelled a backscatterer and it isn't as much of a drain on resources either.

I haven't been able to leave it configured as a potential backscatterer any way because I don't make config changes without checking everything that I think the change even may effect immediately the changes are committed and I did not like the rejection message it made so it has spent a grand total (three attempts to fix reject message) of about 5 minutes configured so foolishly and the logs for those three very short periods did not record incoming emails aside from my own tester mail.

Just incredible to me that anybody thinks it is OK to have [s]it[/s] anything reveal any (basically) private mapping at any time for any reason to anybody who does not have su/root access locally.

---

