---
title: "clamscan: Load incredibly high"
date: 2013-10-14
forum: General Help
---

### Post by DJ_Cyberdance on 2013-10-14
Hi all,
I have configured my ubuntu box to collect all user's email from various pop3-accounts and store it in a local imap server. This configuration has been working fine since years. But during the last couple of weeks my ubuntu box keeps on crashing. I found out, that the process of downloading and checking mail takes incredibly long - and requires an exorbitant amount of system resources. Having a closer look at the process list I found out that it seems to be the clamscan process which takes about a minute to complete for each downloaded mail message. During that time the clamscan process uses almost 100% of CPU power:

```
21805 ubrnp     20   0  181m 161m 2180 R 99.3 33.1   0:08.98 clamscan
```

This is independend of the size of the downloaded message. Execution of getmail below took almost 20 minutes. Also, the spamassassin process seems to be slower than usual. Note that I haven't changed any configuration lately.

```
getmail version 4.24.0
Copyright (C) 1998-2009 Charles Cazabon.  Licensed under the GNU GPL version 2.
SimplePOP3SSLRetriever:xxxxxxxxxxxx@pop.gmx.net:995:
  msg 281/304 (4460 bytes) delivered
  msg 282/304 (33293 bytes) delivered
  msg 283/304 (4027 bytes) delivered
  msg 284/304 (14236 bytes) delivered
   msg 285/304 (7753 bytes) delivered
  msg 286/304 (768756 bytes) delivered
  msg 287/304 (17213 bytes) delivered
  msg 288/304 (1393982 bytes) delivered
  msg 289/304 (2324963 bytes) delivered
  msg 290/304 (60726 bytes) delivered
  msg 291/304 (6606 bytes) delivered
  msg 292/304 (12125 bytes) delivered
  msg 293/304 (6551 bytes) delivered
  msg 294/304 (573531 bytes) delivered
  msg 295/304 (4667 bytes) delivered
  msg 296/304 (3935 bytes) delivered
  msg 297/304 (3158 bytes) delivered
  msg 298/304 (1474732 bytes) delivered
  msg 299/304 (2752446 bytes) delivered
  msg 300/304 (6566 bytes) delivered
  msg 301/304 (15272 bytes) delivered
  msg 302/304 (7826 bytes) delivered
  msg 303/304 (4211 bytes) delivered
  msg 304/304 (7423 bytes) delivered
  24 messages (9508458 bytes) retrieved, 280 skipped
```

As you can see above, I am using getmail/procmail to fetch email from other accounts. getmail/procmail configuration looks like this:
```

[options]
verbose = 1
read_all = 0
delete = 0
message_log = ~/.getmail/getmail.log

[retriever]
type = SimplePOP3SSLRetriever
server = XXXXXXXXXX
username = XXXXXXXXXX
password = XXXXXXXXXX

[destination]
type = MDA_external
path = /usr/bin/procmail
```

```

:0fw:
| /usr/bin/clamassassin
```

Checking the logfiles there is nothing suspicious apart from two lines in the procmail log file:
```

procmail: Couldn't determine implicit lockfile from "/usr/bin/spamassassin"
procmail: Couldn't determine implicit lockfile from "/usr/bin/clamassassin"
```

As mentioned above, this configuration has been working flawlessly for at least 8 years now (using Ubuntu 12.04 LTS at the moment). Does anyone have any suggestions on how to deal with this issue?

---

