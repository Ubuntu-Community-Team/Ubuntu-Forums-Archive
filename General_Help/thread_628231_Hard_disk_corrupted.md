---
title: "Hard disk corrupted"
date: 2007-12-01
forum: General Help
---

### Post by Kobi Haron on 2007-12-01
When I boot, after the GRUB the progress bar starts and then I get the following (some messages are omitted)

[COLOR="Blue"]dev/hdb1: Inodes that were a part of a corrupted orphan linked list found
dev/hdb1: UNEXPECTED INCONSISTENCY: RUN fsck manually (i.e without -a or -p options)
fsck died with exit status 4
.
.
.

* The root file system is currently mounted in read only mode
A maintenance shell shall now be started
.
.
.
bash: no job control in this shell
bash: groups: command not found
.
.
.
-- other bash error messages[/COLOR]

At this stage I get a shell but I have no idea what to do.

Any help will be appreciated. I have Ubuntu 7.10.
[I]
I managed to fix this. I saw in the forums that fsck could be of use. There were many errors which I fixed using the defaults. Then I booted, more errors were discovered and fixed, and I managed to login.

During all my time with Windows I never had anything like that. [/I]

---

