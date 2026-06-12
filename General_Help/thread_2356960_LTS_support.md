---
title: "LTS support"
date: 2017-03-28
forum: General Help
---

### Post by kent-c on 2017-03-28
Hi all,

Just came across something that is confusing me (yup... like that's not hard to do ;)).  

I run 12.04 LTS on my desktop (which I do plan to upgrade in the next coming months) and 15.04 on my laptop.

This morning while updating my desktop, I figured I would check for updates on the laptop.  I have to say that I was surprised that my updates on the desktop went off without a hitch and my laptop is advising me that 15.04 is no longer supported.  I took a look at the settings for the software updater and didn't notice anything out of whack compared to the desktop.

So is this a case of it not being an LTS version or might it be something else?


Thanks in advance,

Kent

---

### Post by deadflowr on 2017-03-28
15.04 was not an lts.
LTS versions are only from even number years from the month of April, so currently those are 12.04 14.04 16.04. And next one will be 18.04.

non-lts releases are only officially supported for 9 months, so your 15.04 system is over a year out-of-date.

You will need to do double release upgrading, as 12.04 ends support next month.
[https://lists.ubuntu.com/archives/ubuntu-announce/2017-March/000218.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2017-March/000218.html")

Good luck on the upgrades, when you do them.

---

### Post by kent-c on 2017-03-28
Thanks, i thought it may be something like that but I couldn't find anything on Ubuntu's site.

I appreciate the quick reply.

Kent

---

### Post by Impavidus on 2017-03-28
For the laptop I would try a clean install. A double release upgrade via an unsupported release is more likely to end in a disappointment.

On the desktop a release upgrade will give you 14.04, which will be supported for two more years, so so can stick to that for a while. Or try a double release upgrade (a bit risky) or a fresh install. I've done many upgrades and they generally worked well, but the more releases you try to jump, the larger the probability that it doesn't work as intended.

---

