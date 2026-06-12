---
title: "rsync works..grsync doesn't"
date: 2015-06-16
forum: General Help
---

### Post by leeelson on 2015-06-16
The following works:
rsync -r -n -t -v --delete -u --modify-window=1 /home/elson/mnt/Lee/AppData/roaming/Thunderbird/Profiles/5vszinu9.default/*.mab /home/elson/.thunderbird/9lqpauov.default/
When done with grsync, I get:
**** thunderbird - Tue Jun 16 10:36:31 2015

** Launching RSYNC command (simulation mode):
rsync -r -n -t -v --delete -u --modify-window=1 /home/elson/mnt/Lee/AppData/roaming/Thunderbird/Profiles/5vszinu9.default/*.mab /home/elson/.thunderbird/9lqpauov.default/

sending incremental file list
rsync: link_stat "/home/elson/mnt/Lee/AppData/roaming/Thunderbird/Profiles/5vszinu9.default/*.mab" failed: No such file or directory (2)

rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]
sent 18 bytes  received 12 bytes  60.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)
Rsync process exit status: 23



Any help is appreciated.

---

### Post by papibe on 2015-06-16
Hi leeelson.

I haven't used grsync in a while, but it looks like it is not expanding the wildcard character so it is taking it literally.

I'm not sure if there's an option to enable it, but you could use the include, or include-from rules to overcome this apparent limitation.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by leeelson on 2015-06-18
> **papibe said:**
> Hi leeelson.

I haven't used grsync in a while, but it looks like it is not expanding the wildcard character so it is taking it literally.

I'm not sure if there's an option to enable it, but you could use the include, or include-from rules to overcome this apparent limitation.

Hope it helps. Let us know how it goes.
Regards.

I kinda thought that might be the case. None of the grsync options seem to address wildcards which makes include difficult to use. I guess I'll just stick to rsync.

Thanks for the help.

---

