---
title: "Any of these can i delete (/var is full)"
date: 2020-06-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-06-10
**/var/cache/archives is a separate partition

```
ls -lh /var/lib/snapd/snaps
total 846M
-rw------- 1 root root  55M May 14 10:26 core18_1754.snap
-rw------- 2 root root  54M May 20  2019 core18_941.snap
-rw------- 2 root root  90M May 20  2019 core_6818.snap
-rw------- 1 root root  94M May 14 10:26 core_9066.snap
-rw------- 2 root root  36M May 20  2019 gtk-common-themes_1198.snap
-rw------- 1 root root  63M May 14 10:27 gtk-common-themes_1506.snap
-rw------- 2 root root 457M May 20  2019 wine-platform_128.snap
```

```
ls -lh /var/log/journal/d2cb2948289a48bc9730282be11218ee
total 257M
-rw-r-----+ 1 root systemd-journal 320K Jun 10 21:59 system@0005a7c55105f667-ba8821cba6126540.journal~
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 20:51 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000049bf7-0005a7c44f74ceb2.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 20:54 system@68fc148842cd43ca82c1e1629e32bb0c-000000000004c0fd-0005a7c45c537387.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 20:57 system@68fc148842cd43ca82c1e1629e32bb0c-000000000004e603-0005a7c467d74929.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:01 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000050b09-0005a7c47339d2d9.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:05 system@68fc148842cd43ca82c1e1629e32bb0c-000000000005300f-0005a7c481dfd24c.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:09 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000055515-0005a7c48ffb50cf.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:12 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000057a1b-0005a7c49c5089a1.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:15 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000059f3f-0005a7c4a7ee1f45.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:18 system@68fc148842cd43ca82c1e1629e32bb0c-000000000005c451-0005a7c4b1712584.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:21 system@68fc148842cd43ca82c1e1629e32bb0c-000000000005e961-0005a7c4bb7ff063.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:24 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000060e67-0005a7c4c7f15e20.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:28 system@68fc148842cd43ca82c1e1629e32bb0c-000000000006337a-0005a7c4d3eafc7f.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:31 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000065880-0005a7c4e08335cc.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:34 system@68fc148842cd43ca82c1e1629e32bb0c-0000000000067d8c-0005a7c4ec9d02ca.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:38 system@68fc148842cd43ca82c1e1629e32bb0c-000000000006a29f-0005a7c4f6d1ce25.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:41 system@68fc148842cd43ca82c1e1629e32bb0c-000000000006c7b5-0005a7c5045a5637.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:44 system@68fc148842cd43ca82c1e1629e32bb0c-000000000006ecc9-0005a7c51026f4c7.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:47 system@68fc148842cd43ca82c1e1629e32bb0c-00000000000711e6-0005a7c51b834056.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:57 system@eddfa4ddb74d42538c071166a5e18e25-0000000000000001-0005a7c525667ce5.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:57 system@eddfa4ddb74d42538c071166a5e18e25-0000000000002507-0005a7c530b3b4b0.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:59 system@eddfa4ddb74d42538c071166a5e18e25-0000000000004a0d-0005a7c542b15afb.journal
-rw-r-----+ 1 root systemd-journal    0 Jun 10 22:35 system.journal
-rw-r-----+ 1 root systemd-journal    0 Jun 10 21:59 user-1000@0005a7c5510284ca-324f083c520ae61d.journal~
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:59 user-1000@480774b52a474c3488eed6627b052727-0000000000079c20-0005a7c54c607e07.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:12 user-1000@c4ffc4de511342f4aaa633d33749e219-0000000000058277-0005a7c4a0044225.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:15 user-1000@c4ffc4de511342f4aaa633d33749e219-000000000005a61f-0005a7c4a94c19d1.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:17 user-1000@c4ffc4de511342f4aaa633d33749e219-000000000005c7e3-0005a7c4b259879f.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:22 user-1000@c4ffc4de511342f4aaa633d33749e219-0000000000061160-0005a7c4c9ae2af8.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:31 user-1000@c4ffc4de511342f4aaa633d33749e219-0000000000067482-0005a7c4e9db1519.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:34 user-1000@c4ffc4de511342f4aaa633d33749e219-0000000000068c3f-0005a7c4f05c2166.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:37 user-1000@c4ffc4de511342f4aaa633d33749e219-000000000006b3ef-0005a7c4fdbbd968.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:41 user-1000@c4ffc4de511342f4aaa633d33749e219-000000000006d7a9-0005a7c509a35f8c.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:44 user-1000@c4ffc4de511342f4aaa633d33749e219-000000000006ef6d-0005a7c510df90bc.journal
-rw-r-----+ 1 root systemd-journal 8.0M Jun 10 21:47 user-1000@c4ffc4de511342f4aaa633d33749e219-0000000000071313-0005a7c51ba895be.journal
```

i believe i just need to make the partition larger, but i am lazy and do not want to wait a on data transfers to rearrange partitions

---

### Post by Holger_Gehrke on 2020-06-11
snap likes to keep older revisions as backups. You can see the revisions using 'snap list -all' and remove the old ones with 'snap remove --revision revision_number snap_name'.

For the journal you can reduce the file sizes using 'journalctl' with the --vacuum-size, --vacuum-time or --vaccum-files options to reduce the size of archived journals. There are also several options in /etc/systemd/journald.conf to set limits to the growth of these files.

Holger

---

### Post by pqwoerituytrueiwoq on 2020-06-11
snapd is not even installed, guess i can deleted it all then
aside from rebooting is there a way to get the my newly acquired free space to be available?
every time i have ever ran out of space and deleted something it took a reboot to get the disk space back

---

### Post by ActionParsnip on 2020-06-11
Is the system a VM? If so, power it off and make a snapshot/checkpoint, power it on and delete the files. See what happens

---

### Post by pqwoerituytrueiwoq on 2020-06-12
I deleted it, not a VM, no issies

---

