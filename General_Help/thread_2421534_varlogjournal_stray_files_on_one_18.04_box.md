---
title: "/var/log/journal stray files on one 18.04 box?"
date: 2019-06-23
forum: General Help
---

### Post by kpatz on 2019-06-23
I tried doing a search but didn't find much other than "/var is full" posts, so I was wondering what is in /var/log/journal and do I care about these files?  They aren't the usual text log files, as they are large and aren't readable in a text editor.

Also, on one of my boxes they may not be cleaning out properly, and are taking up over 1.5 GB of space.  I'll keep an eye over the next few days to see if they change.

On one 18.04 box (running desktop), /var/log/journal appears to be behaving:```

kpatz@catzfs01:/var/log/journal/ce8432777d774eda8257fa6ec5a224ae$ ls -l
total 221196
-rw-r-----+ 1 root systemd-journal 125829120 Jun 12 20:41 system@402c175724b2443eae6a1f75af7dd0f5-0000000000000001-00058a37d3ad02fa.journal
-rw-r-----+ 1 root systemd-journal  50331648 Jun 23 08:29 system.journal
-rw-r-----+ 1 root systemd-journal  41943040 Jun 23 08:30 user-1000.journal
-rw-r-----+ 1 root systemd-journal   8388608 Jun  5 08:24 user-1001.journal
kpatz@catzfs01:/var/log/journal/ce8432777d774eda8257fa6ec5a224ae$ 
```On my other 18.04 box, which is my firewall and running Ubuntu Server, no GUI, there's more files in there, perhaps old ones aren't getting cleaned out?

```
kpatz@catzfw01:/var/log/journal/61bcded376a34427a58895edbb5d2889$ ls -l
total 1540168
-rw-r-----+ 1 root systemd-journal  67108864 Jun  6 14:54 system@fcead388983f4f5784064ab1cb2e788e-00000000000669e3-00058a7caa608c91.journal
-rw-r-----+ 1 root systemd-journal  58720256 Jun  8 21:42 system@fcead388983f4f5784064ab1cb2e788e-0000000000089237-00058aac40224c90.journal
-rw-r-----+ 1 root systemd-journal  58720256 Jun 11 04:52 system@fcead388983f4f5784064ab1cb2e788e-00000000000aa72a-00058ada2b7c1429.journal
-rw-r-----+ 1 root systemd-journal  67108864 Jun 13 12:52 system@fcead388983f4f5784064ab1cb2e788e-00000000000cbebb-00058b086c0ec32b.journal
-rw-r-----+ 1 root systemd-journal  67108864 Jun 15 21:22 system@fcead388983f4f5784064ab1cb2e788e-00000000000ee5d5-00058b375bd2d202.journal
-rw-r-----+ 1 root systemd-journal  58720256 Jun 18 03:54 system@fcead388983f4f5784064ab1cb2e788e-0000000000110541-00058b66b51523e5.journal
-rw-r-----+ 1 root systemd-journal  67108864 Jun 20 10:25 system@fcead388983f4f5784064ab1cb2e788e-000000000013172f-00058b946aaa92c8.journal
-rw-r-----+ 1 root systemd-journal  67108864 Jun 22 17:18 system@fcead388983f4f5784064ab1cb2e788e-00000000001536e9-00058bc21d454d63.journal
-rw-r-----+ 1 root systemd-journal  25165824 Jun 23 08:33 system.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun  6 14:54 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-00000000000669e2-00058a7caa5f6df1.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun  8 21:42 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-0000000000089234-00058aac402152dd.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 11 04:52 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-00000000000aa71f-00058ada2b7a9849.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 13 12:52 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-00000000000cbead-00058b086c0dddc7.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 15 21:22 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-00000000000ee5d2-00058b375bd1ae22.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 18 03:54 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-0000000000110538-00058b66b514263e.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 20 10:25 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-000000000013172b-00058b946aa980da.journal
-rw-r-----+ 1 root systemd-journal 125829120 Jun 22 17:18 user-1000@74d5b9c849ba41bf8e4990b79ce5b9d4-00000000001536e7-00058bc21d440690.journal
-rw-r-----+ 1 root systemd-journal  33554432 Jun 23 08:33 user-1000.journal
kpatz@catzfw01:/var/log/journal/61bcded376a34427a58895edbb5d2889$ 

```

Thoughts?  Are these safe to delete?  And why are they self cleaning on one box and not on another?

---

### Post by deadflowr on 2019-06-23
Use journalctl commands to clear out old journal logs.
I periodically use --vacuum-time=1d to clear out all except those for today
Check the disk-usage
```
journalctl --disk-usage
```
clear out older logs
```
sudo journalctl --vacuum-time=1d
```
There are plenty of more options to choose from including flushing and rotating logs which move logs from /run to /var and from active state to inactive state, respectively.
See journalctl -h for more.

Here's a thread on it over at stackexchange:
[https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl]("https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl")
For more references.

---

### Post by kpatz on 2019-06-23
**journalctl --disk-usage** just told me how much space the journal files were taking up (1.5G on the firewall system and 216M on the file server).

I ran **sudo journalctl --vacuum-time=1d** on the firewall and it deleted the archived journals and now they're only taking up 88M.  But why is the firewall keeping so much more journal data than the file server?  The firewall has been running a bit longer than the file server (by a few weeks, I upgraded it first).

Looks like there's settings in /etc/systemd/journald.conf to tell it to only use up to a certain amount of space, but there appears to be no defaults.  Does this mean, by default, it can just fill up all the space, and it never deletes old journals?

I'll have to keep an eye on it.  Thanks for the info.

---

