---
title: "Evolution stops downloading pop mails"
date: 2014-07-15
forum: General Help
---

### Post by Marcelo Ruiz on 2014-07-15
Hi All.
I am having a really annoying problem with Evolution 3.10.4 x64. It starts downloading messages from the pop3 server (Yahoo) but suddenly stops and says it cannot download this particular email:

```
Cannot get message AC/kimIAABqDUw3H9wAAADNdlMU: Unknown reason
```

Even identifying the message and erasing it (and also the previous and the following)  from the server does not help.
I also tried shutting down evolution with --force-shutdown, and deleting all the .cmeta, .index, .data files and the folders.db. After that I started evolution offline (--offline) and closed it (this regenerates the deleted files) and opened it once again (CAMEL_DEBUG=all evolution >& evo_debug.log) to work online the message changed to:

```
Cannot get message AO3kimIAABraUw2u3QAAADgQRjM: Unknown reason
```

So, even with the offending message gone (and its neighbors too for extra caution), I cannot get rid of this annoying message and Evolution won't download any more e-mails from my account.

The log file I get is attached.

I would really appreciate any help with this annoying issue.

For the record: I can't use IMAP so that's not an option, and I can't use another program (like Thunderbird).

Thanks!

---

### Post by Marcelo Ruiz on 2014-07-16
Ok, one thing that I found out is that Yahoo Servers might be limiting pop3 clients to download messages newer than 1 year.
Basically, when Evolution (or Thunderbird) contact the yahoo pop server, the servers responds that it has a number of emails (let's say 300). The program will start downloading the messages starting from the most recent one #300 and keeps going down until it counts those 300 messages that the server informed it had. The problem is that if message #256 is older than 1 year, the server will interrupt the communication with the program, and the program will display that I can't retrieve the message for 'unknown reasons'.
I think this is the problem because the new Yahoo webmail client does not allow me to browse for messages older than 1 year, and the last message I see in that list is the very same one Evolution retrieves before failing.
To make things worse, if you happen to have a free yahoo account, good luck with contacting customer (don't) care.

---

