---
title: "File system with errors - inode seems to contain garbage AFTER Timeshift"
date: 2023-04-03
forum: General Help
---

### Post by 777funk on 2023-04-03
i went into Timeshift to create a backup snapshot (to the same drive as the OS) and it would not do it. The program just seemed to do nothing and go back to the main screen after I hit "take snapshot". So I figured maybe since I already had 3 snapshots, I needed to delete one. I went to delete one of the snapshots and it seemed very slow and was pretty much freezing the rest of the system (couldn't do anything) so I hit power and it shut down. 

Now I can't boot. I'm getting:

dev/sda5 (Xubuntu ext4 main partition on a dual boot system) Unexpected Inconsistency: Run fsck Manually

fsck exited with status code 4
 Failure: File system check of the root file system failed
Inode 6565313 seems to contain errors


Is there anything I can do beside reinstall? I have a good amount of time setting this system up for audio.

---

