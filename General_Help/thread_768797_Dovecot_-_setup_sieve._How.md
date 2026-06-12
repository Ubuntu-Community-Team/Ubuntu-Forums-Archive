---
title: "Dovecot - setup sieve. How?"
date: 2008-04-26
forum: General Help
---

### Post by Versusnja on 2008-04-26
Hi!

I'm running dovecot server on gutsy. Everything works well: SSL, userdb on MySQL. I'm quite happy with Dovecot.

but I want to get dovecot-sieve plugin working. I spent hours on reading dovecot's wiki, but no luck. I can't see any errors related to sieve in dovecot log, neither the messages are sorted.
So, nothing happens at all. Dovecot works as usually. No sign of message filtering.

What did I do to setup sieve:
1. uncommented *mail_plugins = cmusieve* in configuration file
2. created *.dovecot.sieve* file with a sample dovecot script inside in mail user directory
3. restarted dovecot, tried sieve

no result.

Then I set sieve variable via mysql, tried that, no luck.

if anybody have configured sieve successfully, please share your experience.

---

