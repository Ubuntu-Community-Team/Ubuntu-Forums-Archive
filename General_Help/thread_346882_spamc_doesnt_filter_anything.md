---
title: "spamc doesnt filter anything"
date: 2007-01-26
forum: General Help
---

### Post by tag on 2007-01-26
I just installed my postfix, spamassassin, cyrus imap solution on my 6.06 Dapper LTS box and it all works fine up until the point where I want to use the spamc+spamd combination instead of the big'ol spamassasin perl skript.

I created a /etc/spamassassin/spamc.conf file and set it to:

-d 127.0.0.1
-p 783
-s 3500000

a quick "ps -aux|grep spamd" shows that spamd is running on his own user acc:

root     27712  0.0  1.8  69448 38504 ?        Ss   Jan24   0:00 /usr/sbin/spamd --daemonize --username spamd --ip-address=127.0.0.1 --create-prefs --max-children 5 --helper-home-dir -d --pidfile=/home/spamd/spamd.pid
spamd    27723  0.0  1.8  71728 37880 ?        S    Jan24   0:00 spamd child
spamd    27724  0.0  1.8  69448 37172 ?        S    Jan24   0:00 spamd child

I can even see the port is open

PORT    STATE SERVICE
25/tcp  open  smtp
143/tcp open  imap
783/tcp open  spamassassin

but when I do a quick test, like
cat mail.txt| spamc
i just get my email echoed back without any changes in the headers. spamassassin --lint gives not warnings, and when I do a

cat mail.txt|spamassassin

I usually get my email echoed back with new headers (as it should be)

----[snip]---------------------
X-Spam-Score: 7.4
X-Spam-Flag: YES
X-Spam-Checker-Version: SpamAssassin 3.1.0 (2005-09-13) on ubuntu60664m
X-Spam-Level: *******
X-Spam-Status: Yes, score=7.4 required=5.0 tests=AWL,DATE_IN_PAST_12_24,
DRUGS_ERECTILE,DRUGS_ERECTILE_OBFU,RCVD_IN_BL_SPAMCOP_NET,RCVD_IN_XB
----[snip]---------------------

So my question is: Why doesn't spamc+spamd work?

regards,
Eddy

---

### Post by tag on 2007-01-26
Okay, turns out my client wasn't allowed to connect to the server. To allow Client IPs for a particular server just add "-A <IP-ADRESS>" to the spamd options.

regards

---

