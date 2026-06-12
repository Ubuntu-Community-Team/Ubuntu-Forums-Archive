---
title: "postfix / pflogsumm broken again?"
date: 2008-05-14
forum: General Help
---

### Post by cnschulz on 2008-05-14
Hi, 

Im seeing that my pflogsumm is incorrectly reporting messages as deferred when they have actually been delivered.

Im using hardy server with postfix 2.5.1 and pflogsumm 1.1.0 (with the patch)

I have tracked down the problem to messages that have a conn_use of 1 (that is, the conn_use entry is *not* in the log listing)

here is an example of a message that *is* listed as sent:

May 14 00:01:05 zoidberg postfix/smtp[28326]: 195861B8073: to=<xxx@hotmail.com>,     relay=mail.xxx.com.au[xxx.xxx.xxx.xxx]:25, conn_use=33, delay=603, delays=561/40/0.07/0.94, dsn=2.0.0, status=sent (250 2.0.0 m4DE0Ie2002528 Message accepted for delivery)

and one that is listed as deferred (incorrectly)

May 14 00:05:26 zoidberg postfix/smtp[28796]: D06984180F1: to=<xxx@mac.com>,          relay=mail.xxx.com.au[xxx.xxx.xxx.xxx]:25,              delay=904, delays=901/0.02/1.8/0.88, dsn=2.0.0, status=sent (250 2.0.0 m4DE5GpR008404 Message accepted for delivery)

and here is the regex that i think is at fault

elsif((($addr, $relay, $delay, $status, $toRmdr) = $logRmdr =~
		/to=<([^>]*)>, (?:orig_to=<[^>]*>, )?relay=([^,]+), (?:conn_use=[^,]+, )?delay=([^,]+), (?:delays=[^,]+, )?(?:dsn=[^,]+, )?status=(\S+)(.*)$/o) >= 4)

any ideas?

c.

---

