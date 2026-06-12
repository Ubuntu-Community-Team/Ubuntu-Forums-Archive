---
title: "Rsync problems with computers in different timezones"
date: 2006-11-05
forum: General Help
---

### Post by aparsons on 2006-11-05
I have an rsync command to syncronize two computers (1 computer is in CST and the other is in EST).

However, when using the -u flag, it seems to re-sync my two computers because the timestamps are different, which is annoying when you have 60gb going across the country.

Here is my command:
rsync -vurt --progress --delete /data/music/ root@aphbgfs01:/data/music/ > /data/scripts/rsync_music.log

Any help would be greatly appreciated.

---

