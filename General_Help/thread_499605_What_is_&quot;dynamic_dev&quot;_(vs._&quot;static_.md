---
title: "What is &quot;dynamic /dev&quot; (vs. &quot;static /dev&quot;) ?"
date: 2007-07-12
forum: General Help
---

### Post by xp_newbie on 2007-07-12
What is dynamic /dev (vs. static /dev) ?

I saw these two terms for the first time here:

[http://doc.gwos.org/index.php/Lm-sensors_hddtemp]("http://doc.gwos.org/index.php/Lm-sensors_hddtemp")

And I am curious: How do I know whether my Ubuntu 6.06 has dynamic /dev or static /dev ?

Please note: I am not asking how to setup lm-sensors, but rather asking to understand what "static /dev" vs. "dynamic /dev" means.

I combed the web for an answer and it seems that Google knows nothing about this issue. :(

Thanks,
Alex

---

### Post by astoltz on 2007-07-12
I have only a general idea, but...

In a dynamic /dev, the device nodes don't get created until they are needed.  For example, on my system, there are no /dev/sd* device nodes until I plug in a USB drive.  Then they get created as needed to suit the drive (/dev/sda1 for the first partition, etc.).  I believe a dynamic /dev system has been the standard on Ubuntu since very early, maybe even from the start.

---

