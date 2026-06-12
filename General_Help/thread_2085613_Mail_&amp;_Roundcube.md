---
title: "Mail &amp; Roundcube"
date: 2012-11-18
forum: General Help
---

### Post by davidgutu on 2012-11-18
Hi,
I'm stuck. I normally use mailutils mail command to view my mail and it'll spit out somehting like:
```

root@hostname:/etc/postfix#   mail
"/var/mail/root": 24 messages 24 unread
>U   1 Anacron            Sun Jul 22 07:59  16/565   Anacron job 'cron.daily' on hostname
 U   2 Anacron            Sun Jul 29 10:46  15/539   Anacron job 'cron.daily' on hostname
 U   3 Anacron            Sun Aug  5 08:31  15/539   Anacron job 'cron.daily' on hostname
 U   4 Anacron            Sun Aug 12 08:17  15/539   Anacron job 'cron.daily' on hostname
 U   5 Anacron            Sun Aug 19 08:07  15/539   Anacron job 'cron.daily' on hostname
 U   6 ogutu@hostname   Mon Aug 20 07:12  16/579   *** SECURITY information for hostname ***
 U   7 Anacron            Sun Aug 26 07:47  15/539   Anacron job 'cron.daily' on hostname
 U   8 Mail Delivery Syst Tue Aug 28 21:43  74/2334  Undelivered Mail Returned to Sender
 U   9 Mail Delivery Syst Tue Aug 28 21:43  74/2334  Undelivered Mail Returned to Sender
 U  10 Anacron            Wed Sep  5 19:46  15/540   Anacron job 'cron.daily' on hostname
 U  11 Anacron            Fri Sep  7 18:32  15/540   Anacron job 'cron.daily' on hostname
 U  12 Anacron            Mon Sep 10 15:31  15/540   Anacron job 'cron.daily' on hostname
 U  13 Anacron            Tue Sep 11 09:30  15/540   Anacron job 'cron.daily' on hostname
 U  14 Anacron            Mon Sep 17 08:21  15/540   Anacron job 'cron.daily' on hostname
 U  15 Anacron            Sun Sep 23 09:43  15/540   Anacron job 'cron.daily' on hostname
 U  16 Anacron            Mon Sep 24 07:52  15/540   Anacron job 'cron.daily' on hostname
 U  17 Anacron            Wed Oct  3 12:50  15/540   Anacron job 'cron.daily' on hostname
 U  18 Anacron            Sun Oct  7 11:58  15/540   Anacron job 'cron.daily' on hostname
 U  19 Anacron            Wed Oct 17 18:25  15/540   Anacron job 'cron.daily' on hostname
 U  20 Anacron            Fri Oct 26 07:39  15/540   Anacron job 'cron.daily' on hostname
 U  21 Anacron            Mon Oct 29 09:41  15/540   Anacron job 'cron.daily' on hostname
 U  22 ogutu@hostname   Mon Oct 29 13:34  16/576   *** SECURITY information for hostname ***
 U  23 Anacron            Sat Nov 10 20:39  15/540   Anacron job 'cron.daily' on hostname
 U  24 Anacron            Sun Nov 11 07:41  15/540   Anacron job 'cron.daily' on hostname

```

I wanted to use a web interface for this so I followed these instructions: [https://help.ubuntu.com/community/Roundcube](https://help.ubuntu.com/community/Roundcube) to get roundcube up and running.

It's up but I cannot log in. I get a login page try to enter my normal username and password but cannot view mail. Is there something special I should do? Should I use the same username/password as I use during login?

Also, please note that I had earlier {~1year ago} used tasksel to install a mail server. I have checked ubuntu db created by roundcube but it still has an empty user table.

Please help.

Thanks!

---

### Post by Cheesemill on 2012-11-18
Roundcube connects to your mail server using either the IMAP or POP protocols.

If you don't have an IMAP or POP server installed on your system then you won't be able to use Roundcube to view your mail.

---

### Post by davidgutu on 2012-11-18
Awesome. Thanks. Got it working after installing a POP server. I now have another problem. I cannot receive email but I can send out. I receive the following error:

 Relay access denied (state 13).

---

