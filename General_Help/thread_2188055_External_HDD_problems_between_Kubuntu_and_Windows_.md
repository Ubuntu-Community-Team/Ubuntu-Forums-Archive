---
title: "External HDD problems between Kubuntu and Windows 7"
date: 2013-11-15
forum: General Help
---

### Post by marcovo on 2013-11-15
Hi all,

To clarify the setting I'm in: originally (like since about 5 years ago) I had windows XP and (k)ubuntu running in dual boot on my PC. Of these, I used windows most frequently. After a while I bought an external 2TB HDD, which I used primarily with XP, and sometimes with kubuntu (which worked fine).
After a while (a few months ago) my XP HDD crashed, so I switched to Kubuntu for a few months. I set up the extHDD so kubuntu would be able to run a local webserver with my website-files on the extHDD (including f.e. chown -R marco:marco).
Now recently my XP HDD was replaced by a windows 7 HDD. Win7 complained about not having permission to write to my extHDD, so I made some configurations which solved these problems.

However, this morning, booting kubuntu again, (nearly) all files were changed ownership to root:marco (opposed to marco:marco). Not thinking too hard about it, I again ran chown -R marco:marco over the entire disk.

And now the problem. Some particular files have now become inaccessible, being not able to either read them or write to them. I repeatedly get this error: 'Invoer-/uitvoerfout' (Which is dutch, and translates to 'Input/output error').

I reckoned it would not be a problem sharing a harddisk between 2 operating systems, but I guess it probably is a problem... so my questions now are:
 - how do I solve these input/output errors? I hope without losing any data?
 - is it possible to -safely- share my external HDD between win7 and Kubuntu?

Currently I'm running Kubuntu 12.04.

Many thanks!

Regards,
Marco

---

