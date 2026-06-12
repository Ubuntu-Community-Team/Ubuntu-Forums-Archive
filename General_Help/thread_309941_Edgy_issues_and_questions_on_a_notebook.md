---
title: "Edgy issues and questions on a notebook"
date: 2006-11-30
forum: General Help
---

### Post by scifan on 2006-11-30
I have an Acer 5672 that I was running Dapper on... many things seemed to function correctly... Last week I decided to update to Edgy.

First... could someone explain why "df" doesn't show my root filesystem any longer?  The /etc/fstab has this line "UUID=6D54-FF80 / ext3 defaults,errors=remount-ro 0 1" instead of "/dev/sda3 / ext3 defaults,errors=remount-ro 0 1" which appears to work as I can SEE files stored in that partition, but it doesn't show up when I run a "df -h"...

Second... my kids helped me by shutting my notebook the other day.  The notebook didn't hibernate as I thought I'd configured in the power management tool... (didn't hibernate when power was attached under Dapper either).  What it did do that was very obnoxious was the video driver started having a flicker on the bottom 1/3 of my screen... my notebook is an Acer Aspire 5672 with an ATI X1400 video card.  I've installed the ati drivers and know that it's a very obnoxious occurence... I didn't experience this with previous configurations.

Could anyone point me at answers for either of the above issues? 

Thanks

---

### Post by gborzi on 2006-11-30
I can help with the first issue. The UUID is a unique identifier for partitions, which is useful when you change the physical location of your hard disk inside the PC. For exampled, if you move your ide hd from channel 0 to channel 1, the old partition names will change from hdaX to hdcX, and your fstab cannot work. With the UUID this is no longer a problem, because the fstab remains the same regardless of the physical location of the hd. This issue has been discussed on mailing lists, you can find links to the discussion by searching UUID in the forums.

---

