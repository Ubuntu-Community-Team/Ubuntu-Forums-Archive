---
title: "How to mount ftp? -OR - How on earth do you get LUFS working??"
date: 2005-10-19
forum: General Help
---

### Post by One Quick Question on 2005-10-19
Ok, so, I need to mount some ftp sites. After much Googling, I have come to install lufs-utils and lufs-source.  I compiled and installed the module with no errors, but when I tried to modprobe it, I got this FATAL message:
```
FATAL: Error inserting lufs (/lib/modules/2.6.10-5-386/kernel/fs/lufs.ko): Invalid module format
```
Notice how the first word is in all caps.  That means not just fatal, but FATAL.  
Now then, after more Googling, I came across that oft-quoted part about how LUFS isn't maintained so much, and I must change kill_proc_info to kill_proc.  I did that, and I recompiled and reinstalled using the -f flag on module-assistant.   Same error.
So I'm wondering, is this a different error than the one caused by the kill_proc_info symbol?  Did the edit really fix it but the change is being ignored since I already "installed" it?  Is there a better way than LUFS?  (Using Gnome or KDE magic (or other programs) isn't what I need.)

---

