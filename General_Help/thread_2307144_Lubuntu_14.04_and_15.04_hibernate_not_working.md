---
title: "Lubuntu 14.04 and 15.04 hibernate not working"
date: 2015-12-22
forum: General Help
---

### Post by galapah on 2015-12-22
Hello,
on my laptop I have Lubuntu 15.04. And in it a KVM virtual machine with Lubuntu 14.04. In either case, suspend works fine, hibernate does not.

On the main system, I tried [FONT=courier new]pm-hibernate[/FONT]. It shuts down, but after new start, it does not restore the session.

Now I concentrate on the virtual system first. I tried [FONT=courier new]pm-hibernate[/FONT], the same behaviour as above. 

The end of the [FONT=courier new]/var/log/pm-suspend.log[/FONT] shows this:
```
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 107: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 107: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 107: /sys/class/dmi/id/board_vendor: No such file or directory
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Út pro 22 12:29:58 CET 2015: performing hibernate
```

I have searched for solutions a long time, and I noticed there should be a line containing "Finish" at the end, which cannot be seen in my log.

Then I tried [FONT=courier new]s2disk[/FONT]. It seems to save an image and shuts the computer down. But the system will not start, it hangs.
The [FONT=courier new]/var/log/syslog contains these lines[/FONT]:
```
Dec 22 14:46:31 Archie kernel: [    0.943049] PM: Checking hibernation image partition UUID=41774ce9-7056-4dc1-b991-1c7b8001348b
Dec 22 14:46:31 Archie kernel: [    1.008226] PM: Hibernation image not present or could not be loaded.
```

I am sure that the UUID is the correct swap partition. Also, there is enough space on my swap partition (8 GB swap vs. 6 GB RAM, no swap is being used).

I am stuck here, I have no idea what to do now. I could not find any solution.

---

