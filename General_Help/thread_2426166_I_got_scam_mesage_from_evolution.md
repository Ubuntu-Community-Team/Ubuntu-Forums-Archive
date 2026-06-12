---
title: "I got scam mesage from evolution"
date: 2019-09-05
forum: General Help
---

### Post by marijonas194az on 2019-09-05
how to find why and from ho?
[ATTACH=CONFIG]283936[/ATTACH]

---

### Post by TheFu on 2019-09-07
You probably cannot find who.  All you can find is the hacked servers used to send the email. If you look at the "full headers" and learn to understand the information in there, tracing back to the owner of each server, it will become clear.  If it makes you feel better, you can forward the spam to the "abuse" contact for the source email server internet provider. They won't do anything, since you aren't a customer, the spammers are OR the spammers hacked their network.

Only the TO has to be correct in email headers. It is a practical requirement - since the TO is where email is sent.  The FROM can be almost anything. The standard doesn't have any validation required.

In the mid-1990s and earlier, the email protocol, SMTP, was really simple and worked from any IP in the world.  Then spam email started up, so different techniques have been added attempting to block spam.

Scam messages can only be prevented at the server level if the sending email admin does their job and sets up SPF and blocks sending from non-approved FROM addresses.
AND
the receiving email server takes aggressive steps NOT to accept emails from senders who don't pass SPF validation.

Some email clients can learn what you consider spam and sort those messages into spam/junk folders.  I don't use evolution, but other email clients definitely have this capability.  Servers can pre-filter junk too, if the email admin configures the extra processes to accomplish that.

In theory, DMARC signing was another layer supposed to make sending by spammers harder, but very few server admins use it and it breaks some commonly used email tools like broadcast and re-send listservers.  It isn't too popular, but gmail tries to use it, but doesn't mandate it.  Gmail uses SPF records ...  you can look those up for any domain:
```
dig txt gmail.com
```
the important returned line is:
```
gmail.com.              300     IN      TXT     "v=spf1 redirect=_spf.google.com"
```
which says to get the TXT DNS record for that location:
```
dig txt _spf.google.com]
...
_spf.google.com.   300  IN  TXT "v=spf1 include:_netblocks.google.com include:_netblocks2.google.com include:_netblocks3.google.com ~all"
...

```
I removed uninteresting parts.  The **~all** at the end says that other domains can send email claiming to be from gmail and it shouldn't be blocked.  In effect, making all of Gmail's SPF records next to worthless.  Google allows unknown IPs to send email from any IP in the world.  Generally, that is seen by companies who send out lots and lots of bulk email/marking crap that nobody wants ... which is what google does.  Make sense?

---

### Post by marijonas194az on 2019-09-08
it is strange, because me calendar empty and its firs time i got spam or not spam message in this evolution notification that i geet.

---

