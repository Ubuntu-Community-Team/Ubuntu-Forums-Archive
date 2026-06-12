---
title: "email issue"
date: 2013-02-26
forum: General Help
---

### Post by Spikerok on 2013-02-26
I have set up SMTP email, for some reason some emails I send are not received by the recipient. I get next error:

----- Transcript of session follows -----
... while talking to smtp.europe.secureserver.net.:
DATA
<<< 550 5.7.1 SPF unauthorized mail is prohibited.
554 5.0.0 Service unavailable
Reporting-MTA: dns; www12.securelybuy.com
Received-From-MTA: DNS; [194.75.206.136]
Arrival-Date: Thu, 14 Feb 2013 16:10:21 GMT

Final-Recipient: RFC822; [email]someemail@domain.com[/email]
Action: failed
Status: 5.5.0
Remote-MTA: DNS; smtp.europe.secureserver.net
Last-Attempt-Date: Thu, 14 Feb 2013 16:10:23 GMT

---

### Post by chadk5utc on 2013-02-26
This appears to be settings related from all Ive read. If youll google with quotes the following "550 5.7.1 SPF unauthorized mail is prohibited" you will find a number of links with same issue.
[http://support.godaddy.com/groups/email/forum/topic/550-5-7-1-spf-unauthorized-mail-is-prohibited/](http://support.godaddy.com/groups/email/forum/topic/550-5-7-1-spf-unauthorized-mail-is-prohibited/) From what Ive read you will need to verify your settings to ensure they are compliant.

---

