---
title: "Missing /boot directory"
date: 2014-09-18
forum: General Help
---

### Post by pannir2 on 2014-09-18
I have 4 partitions:

/dev/sda8  - 14.04 LTS
/dev/sda7  - 10.04 LTS
/dev/sda5  - 13.10
/dev/sda2  -  Win XP

I was unable to boot into 10.04 LTS today. My last access was 2 days ago. When I checked /dev/sda7 I noticed that the /boot folder was missing. Is it possible to recover this directory or reinstall without losing my applications?

---

### Post by Impavidus on 2014-09-18
If those partition numbers are correct, you didn't mention all of them. There should at least be an extended partition and sda6. Did you have a /boot partition for your 10.04 system? If you accessed your 10.04 partition from one of your other systems the /boot partition wouldn't get mounted, leaving it empty. Also, 10.04 (except server edition) and 13.10 (and WinXP) have reached end of life. Better not to use them. Unsupported releases – or worse, partially supported releases, like 10.04, which still receives updates for the packages it has in common with the server edition – may break unexpectedly.

---

