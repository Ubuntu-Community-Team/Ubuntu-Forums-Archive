---
title: "Processes hanging around"
date: 2020-08-02
forum: General Help
---

### Post by David_Partridge on 2020-08-02
Did a ps -ef today (2nd August) and saw stuff like this:

```
root      3304   921  0 Jul31 ?        00:00:00 /usr/sbin/CRON -f
root      3306  3304  0 Jul31 ?        00:00:00 /bin/sh -c    mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared && cd /mnt/shared && btrfs-snaps hourly 3 | grep -Ev "$GREPOUT" ; cd / && umount /mnt/shared
root      3308  3306  0 Jul31 ?        00:00:00 mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared
root      3502   921  0 Jul30 ?        00:00:00 /usr/sbin/CRON -f
root      3504  3502  0 Jul30 ?        00:00:00 /bin/sh -c    mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared && cd /mnt/shared && btrfs-snaps hourly 3 | grep -Ev "$GREPOUT" ; cd / && umount /mnt/shared
root      3506  3504  0 Jul30 ?        00:00:00 mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared
root      4140   921  0 Jul27 ?        00:00:00 /usr/sbin/CRON -f
root      4142  4140  0 Jul27 ?        00:00:00 /bin/sh -c    mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared && cd /mnt/shared && btrfs-snaps hourly 3 | grep -Ev "$GREPOUT" ; cd / && umount /mnt/shared
root      4144  4142  0 Jul27 ?        00:00:00 mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared
root      4475   921  0 Jul27 ?        00:00:00 /usr/sbin/CRON -f
root      4476  4475  0 Jul27 ?        00:00:00 /bin/sh -c    mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared && cd /mnt/shared && btrfs-snaps daily  4 | grep -Ev "$GREPOUT" ; cd / && umount /mnt/shared
root      4477  4476  0 Jul27 ?        00:00:00 mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared
root      5233   921  0 Jul27 ?        00:00:00 /usr/sbin/CRON -f
root      5235  5233  0 Jul27 ?        00:00:00 /bin/sh -c    mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared && cd /mnt/shared && btrfs-snaps hourly 3 | grep -Ev "$GREPOUT" ; cd / && umount /mnt/shared
root      5237  5235  0 Jul27 ?        00:00:00 mount -t btrfs -U cf914647-a613-4ced-b3d8-cda423c48ac5 /mnt/shared

```

Doesn't seem right ...  Are they zombie processes? 

David

---

