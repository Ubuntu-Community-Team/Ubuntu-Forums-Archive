---
title: "GPG and evolution"
date: 2008-03-05
forum: General Help
---

### Post by lopezoliver on 2008-03-05
Hi, i've been trying to send signed mails with evolution (already done all necesary with gpg) but i alwas recive this error message form evolution:

Could not create message.

Because "gpg: problem with the agent - disabling agent use
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "763DD5AD oliver xavier lopez corona <lopezoliverx@gmail.com>"
", you may need to select different mail options.

any ideas??

---

### Post by kahukiloia on 2008-03-22
I have exactly the same problem, Have you found a solution yet?

---

### Post by Schpenke on 2008-03-26
Hi there,

I was running in to the exact same problem.  I edited my gpg.conf file located at ~/.gnupg and commented out "use-agent".  After I restarted Evolution my problem seems to have disappeared.  I'd be interested to see whether this fixes your problem as well.

-S

---

### Post by greybeard95a on 2008-04-18
I don't know about the other user, but this worked for me.

---

