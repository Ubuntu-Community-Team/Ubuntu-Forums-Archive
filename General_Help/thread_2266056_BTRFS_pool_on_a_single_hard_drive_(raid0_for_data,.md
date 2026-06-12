---
title: "BTRFS pool on a single hard drive (raid0 for data, raid1 for metadata) and rsync back"
date: 2015-02-19
forum: General Help
---

### Post by kudumi on 2015-02-19
[COLOR=#000000][FONT=-apple-system-font]I'm planing to revamp my existing personal server (3x4TB) with BTRFS. I'm planing to setup a cron job to backup (to a 1x4TB) important data (personal picture, videos etc) but not everything.[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]
[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]Since it's a personal server, I'm opting for RAID0 for data (RAID1 for metadata) and manually/automatically backup important data to a remote drive. As I'm interested to avoid spinning of all hard drives and not interested to lose all the data (incase of a drive/pool failure), I am planing to create three individual btrfs pools on each drive. But I have the following questions[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]
[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]1) Can I mirror metadata (-m RAID 1) on a single hard drive pool? or anything stupid here?[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]
[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]2) Will I get notification If there is any data corruption? (In case of notification, I can pull back the non-corruption data from my backup)[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]
[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]3) In case of data corruption (and I missed to notice), will rsync copy the corrupted file and replace the original file in my backup?[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]
[/FONT][/COLOR]
[COLOR=#000000][FONT=-apple-system-font]any suggestion for using rsync. thanks[/FONT][/COLOR]

---

