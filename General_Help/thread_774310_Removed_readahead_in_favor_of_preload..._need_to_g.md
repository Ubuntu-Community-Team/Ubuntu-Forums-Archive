---
title: "Removed readahead in favor of preload... need to go back"
date: 2008-04-29
forum: General Help
---

### Post by aashay on 2008-04-29
Long story short - I read somewhere that preload does a better job of prefetching things than readahead. So I removed readahead and also all the files in /etc/rcS.d (I just did 'locate readahead' and removed everything I could find... bad idea!!).
So anyway, I'm messing around with bootchart and was thinking of reverting back to readahead just to see if it would make any difference. I have already removed preload with NO difference in the boot times.
As of now, readahead and readahead-list has been installed. However, /etc/readahead is completely empty. Adding 'profile' to kernel the params in Grub doesn't do anything. So readahead is present but due to the deleted files, is doing nothing. Any help (including just posting the readahead bootup scripts here) would be appreciated.

---

