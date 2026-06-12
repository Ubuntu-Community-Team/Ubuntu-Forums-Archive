---
title: "&quot;Migrating Mailserver: Are there any pitfalls??"
date: 2006-11-28
forum: General Help
---

### Post by Beamerboy on 2006-11-28
I am shortly going to be moving my existing freebsd mailserver to my Edgy server and I was wondering if I should be aware of any potential pitfalls.

The FreeBSD server currently runs postfix and dovecot (dovecot is using Maildir method) and manages multiple domains.  I intend to use the same services on Edgy but I have never done it before so I am concered I might end up with lost or corrupt mail.

Does Dovecot use any integrity checks against Maildir to make sure nothing has been tampered with?  Or will I be safe to simply tar up my Maildir and move it to the new server?

Is it safe to use a backup of my existing postfix config files or are they unlikely to be compatable with Edgy?

Thanks in advance.

Beamerboy
AKA Paladine

---

### Post by Beamerboy on 2006-11-29
Bumping because I can't believe that only 21 people have read this.

Paladine

---

