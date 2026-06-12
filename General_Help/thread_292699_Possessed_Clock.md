---
title: "Possessed Clock"
date: 2006-11-04
forum: General Help
---

### Post by sefs on 2006-11-04
Hi my clock keeps setting itself back by 1 hour each time I reboot.

I have the zone as America/NewYork.  And I cant find an option to see if it has daylight savings time turned on.  How can I set it to the correct time I want that will be maintained thru reboots.

Thanks.

---

### Post by PriceChild on 2006-11-04
Are you dual booting with windows xp?

---

### Post by mo79 on 2006-11-04
You might want to check this:

[http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29")

---

### Post by sefs on 2006-11-04
No not dual-booting but i have vista RC 1 in a VM.

---

### Post by jordilin on 2006-11-04
I have the same problem when dual booting with windows xp. Why is that??

---

### Post by rocknrolf77 on 2006-11-04
> **mo79 said:**
> You might want to check this:

[http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29")

Thank's for this one. An really annoying problem.

---

### Post by Kateikyoushi on 2006-11-04
I would say it is because one system is set as BIOS is using gmt and changes it to local time but the other OS uses the BIOS time as local clock.

---

### Post by sefs on 2006-11-04
It was my timezone I didnt realise there was a selection specific for my location.  In windows i usually would have chosen something related to NY time. After choosing my zone selection it went back to our correct time.

---

