---
title: "OSX Yosemite text messaging feature in ubuntu?"
date: 2014-11-09
forum: General Help
---

### Post by palmen-michiel on 2014-11-09
Hello,

I was wondering, recently apple anounced their new OSX Yosemite, within this OS it is possible to send and receive text messages from your computer. I was wondering, since android phones are kind of linux based, and ubuntu is too. Is it possible that there is some kind of way to do this aswell on ubuntu?

Greetings!

---

### Post by ian-weisser on 2014-11-09
Well, using the 'search' feature in the Software Center, I found several SMS applications. Each available in Ubuntu for years now.
So yes, I'd say it seems quite possible.

---

### Post by llamabr on 2014-11-09
> **ian-weisser said:**
> Well, using the 'search' feature in the Software Center, I found several SMS applications. Each available in Ubuntu for years now.
So yes, I'd say it seems quite possible.

Yes, these:
```
brock@silver:~$ apt-cache search sms | grep SMS
gammu-smsd - SMS message daemon
gnokii-smsd - SMS Daemon for mobile phones
gnokii-smsd-mysql - SMSD plugin for MySQL storage backend
gnokii-smsd-pgsql - SMSD plugin for PostgreSQL storage backend
kannel - WAP and SMS gateway
kannel-dev - WAP and SMS gateway headers and development files
kannel-docs - WAP and SMS gateway documentation
kannel-extras - WAP and SMS gateway extras
kannel-sqlbox - SQL helper application for Kannel WAP and SMS gateway
libgsmsd7 - SMS daemon helper library
libnetsds-kannel-perl - Service Delivery Suite framework - Kannel SMS gateway API
libsms-send-perl - driver-based API for sending SMS messages
python-messaging - SMS/MMS encoder/decoder
smsclient - A program for sending short messages (SM / SMS)
smstools - SMS server tools for GSM modems
brock@silver:~$ 

```

---

