---
title: "Is my computer overworked or is this normal? Useing &quot;iotop&quot; disk monitor"
date: 2021-03-11
forum: General Help
---

### Post by sofasurfer on 2021-03-11
I ran "iotop" disk usage monitor. When pc is sitting idle it continues to show that Firefox, in the "io" column, is 99% and the "disk read" column is between 300 k/s and 400 k/s. All other applications display zero. This seems wrong to me. Is there a problem? Or does the "io" column just say that firefox is 99% of the total input/output because thats the only thing running?

I also have a hard drive question. At one time and couple weeks ago one of the system check programs I used reported that my hard drive was about to fail. Now however every system check I use shows no problem except for "661 bad sectors". So how do I really dind out if I have a bad hard drive?

I have extremely slow startup, program starts, web access and after a while it freezes up.

---

### Post by TheFu on 2021-03-11
661 bad sectors is data loss.  You need hourly backups and plans to replace the storage ASAP. Actually, you should have done this a couple of weeks ago when the first warning happened.  By then, it was already probably too late and you've been losing data ever since.

Firefox could be trying to access corrupted data on parts of the drive that have already failed. 

On a fully working system, without HDD issues, Firefox has all sorts of settings to control how much data it send to the mothership. Some for tracking use, some of providing security  protections, some of replicating password and bookmarks DBs. I think those can be disabled.  Tweak those settings and try again.

---

### Post by ActionParsnip on 2021-03-11
Run a final full backup as soon as you can. The drive is dying. Replace drive, clean install of Ubuntu 20.04 then restore your casual user data from your backups

---

### Post by sofasurfer on 2021-03-11
Wanted to be sure my drive was bad. All I read was that the bad sectors are marked and not used again. But that seemed like a lot of bad sectors for a usable drive. I'll replace it shortly. Nothing life changing on it. A new drive and some more memory and it will be like a new car. Thanks.

---

