---
title: "can't access tty; job control turned off"
date: 2007-03-15
forum: General Help
---

### Post by flapane on 2007-03-15
I used deborphan to delete some libraries I didn't use, and probably synaptic deleted some useful library with the deborphan ones...
probably some lib related to cron or whatever...
While booting it says:
can't access tty; job control turned off

Any shots?

---

### Post by liegerm on 2007-03-15
This is probably no help whatsoever but the only time I've seen this was with an Edubuntu thin client. To resolve, I had to either re-issue security keys for the thin clients to use or add them to the /etc/hosts file on the server. Probably nothing to do with your problem, but that's when I saw the message you mention.

---

### Post by flapane on 2007-03-15
I solved by reinstalling ubuntu-minimal

---

