---
title: "Which file system?"
date: 2022-04-24
forum: General Help
---

### Post by laserburn2 on 2022-04-24
Another Ubuntu LTS, another time to ask yourself the eternal question - which file system to use this time around? I thought that by now there would be consensus on this matter, but no dice.

We are talking about a desktop machine with a single NVMe 1TB drive, all of which will be formatted for Ubunru 22.04, no dual boot. 

For Ubuntu 20.04 I used zfs and was really impressed with how easily I could recover from an auto-made snapshot. On the other hand, I was greatly annoyed when I found out that I don't have space on /boot because the said snapshots ate all the space on bpool. Ubuntu 20.04 installer has made bpool too small, or better to say that Canonical likes updating kernel every bloody week, so snapshots end up eating a lot of space and I had to manually remove them on several occasions. Besides, there was a weird problem that was coming and going where the whole interface would be stuttering, this was most noticeable when watching YouTube. I have no evidence that this was indeed a file system issue, but I never seen something like that before and have no explanation for it. I also didn't like how zfs volumes were not automatically trimmed. I could also not see true memory usage, as zfs memory buffers are not transparent to Linux, but this was no big deal, as earlier Gnome memory leaks were fixed. 

Now, I realize this is a subjective matter, but I'd like to hear other people's arguments on the matter.

---

### Post by Impavidus on 2022-04-24
The default has been ext4 for years and it works for most people. If you want something else, you're expected to know what you're doing.

Support for installing on zfs was only added recently. I think in 20.04 it was still considered experimental, so no surprise that it doesn't always work as expected. Maybe that has changed for 22.04; I haven't read the release notes yet.

---

### Post by GhX6GZMB on 2022-04-24
IMO, for a desktop/laptop installation, ZFS is way over the top. EXT4 is reliable and supported by everything.

---

### Post by HermanAB on 2022-04-25
JFS and XFS are also good options for a desk/lap system.

---

### Post by aug7744 on 2022-04-25
ext2 for boot
btrfs for root
another FS for data partition

---

