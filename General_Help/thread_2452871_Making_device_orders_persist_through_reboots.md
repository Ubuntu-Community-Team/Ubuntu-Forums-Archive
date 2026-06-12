---
title: "Making device orders persist through reboots?"
date: 2020-10-29
forum: General Help
---

### Post by chris230291 on 2020-10-29
Hello. I have several DVB adapters. When I reboot the order can change in /dev/dvb, which causes problems for me in TVHeadend. Is there any way I can force the order to always be the same? 

Thanks,
Chris

---

### Post by SeijiSensei on 2020-10-29
The solution for this when it comes to disks is to use UUIDs rather than /dev/sdX. I don't know if there is an equivalent for DVB adapters. What does "sudo blkid" show?

---

