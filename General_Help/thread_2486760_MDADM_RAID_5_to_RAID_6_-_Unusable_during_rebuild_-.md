---
title: "MDADM RAID 5 to RAID 6 - Unusable during rebuild - Info/Help Request"
date: 2023-05-09
forum: General Help
---

### Post by pictureaday on 2023-05-09
Hello Folks,

I have a new install of Ubuntu 22.04 to which I migrated my raid 5 from my previous system. System provides various docker services, network share, plex, etc. I have decided to upgrade from RAID 5 to RAID 6 by adding a 5th disk to my array. The array seems to be rebuilding just fine at around 45,000 KB/sec but the mounted raid device is unusable. I can do an ls on the root, of the mount but if I do ls /media/raid6-mount/subfolder it basically hangs indefinitely. I did turn off all my docker containers (but only after the reshape started). I did experience this same situation when I recently accidentally removed/re-added a drive in the array (when it was RAID5). I had the same symptoms of an essentially unusable system when that was rebuilding (in the old hardware).
Not sure if it matters but the drives are WD Red NAS Plus at 14TB
My reshape is about 25% done with around 3700 minutes left.

1) Should my mounted folder be this unusable while a reshape is happening? Does this suggest something else is wrong? I was always under the impression that I should still be able to use the raid while a reshape/rebuild was happening with some degraded performance.
2) There are some docker services I'd like to temporarily relocate to another drive such as home assistant. What would be the best way to do this? (Should I stop the reshape and copy stuff over then resume or something else?)

Thanks!


Mod Request: Please relocate this post to the [COLOR=#000000]Server Platforms forum if appropriate.[/COLOR]

---

### Post by MAFoElffen on 2023-05-09
...by (not only) adding a 6th disk, but by also using something like:
```

sudo mdadm --grow /dev/md0 [COLOR=#ff0000]--level=6[/COLOR] --raid-devices=6 --backup-file=/root/raid5backup

```
Right?

I would assume so, But just checking...

I would wait until the reshape is through before using it , and especially before making any changes. Asking to reshape a moving target is a very bad idea. IMHO, That is setting up the the outcome of the reshape for failure.

---

### Post by pictureaday on 2023-05-10
Yes, that's how I did it.
Will do, thanks.

---

### Post by MAFoElffen on 2023-05-11
Has the reshape finished yet? Wondering how it went...

---

