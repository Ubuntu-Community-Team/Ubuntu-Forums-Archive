---
title: "mdadm data only question"
date: 2016-09-01
forum: General Help
---

### Post by arch+ on 2016-09-01
I have a 250GB SSD that boots Lubuntu 16.04 and two 4TB HDDs that I'd like to build a RAID 1 array with.  I'm more concerned with the RAID 1 data.  I have a few questions regarding the scenario of using mdadm in RAID 1 for both 4TB HDDs and the Lubuntu SSD goes down:


[LIST=1]
[*]If I place one of the 4TB HDDs in a USB enclosure, will the data be accessible?
[*]Can I install a fresh version of Lubuntu on the SSD and rebuild the RAID 1 while retaining the data?
[/LIST]

Trying to determine my options for backup and recovery.  Thanks

---

### Post by Jimysbil on 2016-09-01
According to [this]("http://superuser.com/questions/426891/raid-1-on-2-external-hdds") you should be able to create a Raid 1 with your drives as external.
As for your second question I think by using the software solution (mdadm) you could recreate your raid even on an other machine.

---

### Post by arch+ on 2016-09-01
Thanks!  I'll play around with that.  An external 3.5 enclosure may be the better way to go.

---

