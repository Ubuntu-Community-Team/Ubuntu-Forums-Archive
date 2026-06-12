---
title: "Unable to whitelist in Postgrey"
date: 2015-02-04
forum: General Help
---

### Post by terryit3 on 2015-02-04
I am running Ubuntu Server 14.04.1 LTS and trying to add domains to the whitelist for postgrey.

Postgrey is functioning correctly, as in, it's greylisting all incoming emails.

I have added the domains to the /etc/postgrey/whitelist_clients file, and then added the following lines to the /etc/default/postgrey file:

```
POSTGREY_OPTS="--inet=10023 --delay=199 --max-age=35"
POSTGREY_OPTS="$POSTGREY_OPTS --whitelist-clients=/etc/postgrey/whitelist_clients"
POSTGREY_OPTS="$POSTGREY_OPTS --whitelist-recipients=/etc/postgrey/whitelist_recipients"
```

I send an email to my account on the test server (terry@test.myserver.org) from my work email (terry@example.org), but the message from the test whitelisted domain still gets blocked.

Any ideas?

Thanks for any assistance.

---

### Post by TheFu on 2015-02-04
Only the last line gets used. This is std bash/sh scripting.  You need to merge the settings you want into a single line and comment out all the others to prevent confusion.

---

### Post by terryit3 on 2015-02-04
Thanks Fu, I was following an example I found online that had it displayed this way. I'll give it a try tomorrow when I'm back at work.

---

### Post by terryit3 on 2015-02-05
I changed that line in my file to include everything in one line...

POSTGREY_OPTS="--inet=10023 --delay=199 --max-age=35 --whitelist-clients=/etc/postgrey/whitelist_clients"

and all email are still being graylisted. Any other ideas?

---

### Post by TheFu on 2015-02-05
well - did you want to include ```

--whitelist-recipients=/etc/postgrey/whitelist_recipients
```

Also - did you restart postfix and postgrey?

---

### Post by terryit3 on 2015-02-05
I haven't added anything to the whitelist_recipients file, so including it now isn't necessary.

I restarted both postfix and postgrey and still get the following message in my mail.log file:

Feb  5 08:38:26 test postgrey[6346]: action=greylist, reason=early-retry (6s missing), client_name=host68-134.xxx.xxx.xxx.us, client_address=12.34.56.78, sender=noname@domain.org, recipient=terry@test.domain.org

---

### Post by terryit3 on 2015-02-05
After a system restart, it seems to be working correctly.

I get a "test postgrey[1089]: action=pass, reason=client whitelist" message at the start of sending the message in my mail.log

---

### Post by TheFu on 2015-02-05
So ... solved? If so, please use the thread tools to mark it.

---

