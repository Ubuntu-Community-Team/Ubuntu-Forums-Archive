---
title: "unattended-upgrades dont send mail to me"
date: 2021-01-07
forum: General Help
---

### Post by tomeksup on 2021-01-07
Hi all

I have to virtual machines with ubun tu 20.04. On both of them i've installed unattended upgrades and made setup to automatic upgrade and SEND notification mail on specified adres. First machine works properly, i get mail notification.

Second machine do not send mail. I have exact the same configuration as on first machine. Few months ago i changed whole settings of email settings. Probably there is a problem. How to reset mail settings of ubuntu ?

Anyone has an idea ?

---

### Post by TheFu on 2021-01-07
which MTA are you using on each systems?  Maybe copy the config files from the working setup to the non-working one and compare the differences?  Also, check DNS.

---

### Post by tomeksup on 2021-01-07
I compare configs from 1 and 2'nd. They are identical.

---

### Post by TheFu on 2021-01-07
> **tomeksup said:**
> I compare configs from 1 and 2'nd. They are identical.

Well, in my MTA, that won't work. There are differences due to the different hostnames.

But since you've figured this out and haven't answered the other questions, good luck.

---

