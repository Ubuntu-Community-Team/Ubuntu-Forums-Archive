---
title: "[SOLVED] feisty changes bios clock on shutdown and boot"
date: 2007-07-09
forum: General Help
---

### Post by distort on 2007-07-09
Everytime I shutdown my Feisty 7.04, the BIOS clock gets set to Ubuntu's clock minus 2 hours.
Everytime I boot Feisty 7.04, 2 hours are added to the BIOS clock.
This wouldn't be a problem, if I wouldn't need to boot into windows 2000 on that same box occasionally, which always has the wrong time then.

---

### Post by bollix47 on 2007-07-09
In Feisty right click on the time and go to preferences.  Make sure UTC is not checked.

---

### Post by distort on 2007-07-09
Thanks for your answer.
I did as you recommended and found that UTC was not checked.

---

### Post by bollix47 on 2007-07-09
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)
[URL="http://ubuntuforums.org/showthread.php?t=429570&highlight=UTC"]
Other suggestions.[/URL]

---

### Post by distort on 2007-07-10
> **bollix47 said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)


That worked!

Thanks a lot!

---

