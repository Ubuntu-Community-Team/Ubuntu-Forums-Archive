---
title: "Multiple Chrome issues"
date: 2016-12-31
forum: General Help
---

### Post by AlyssaVS on 2016-12-31
Hello,

I have had multiple problems recently with Chrome:
[LIST]
[*]Pages opening very slowly
[*]Unable to view videos or they constantly hang up or stop
[*]LastPass extension won't open and cannot access "options" or see "details" to troubleshoot
[*]Error message on startup that Chrome wasn't closed properly when it was
[*]Multiple error messages on startup to "unlock keyring" (used to bypass it because it was just one, now there are three or more)
[/LIST]

Have tried to troubleshoot through disabling unnecessary/unused extensions and clearing browser data but that has not helped. Should I consider re-installing Chrome? Or is there a known issue out there that I am unaware of?

Running Ubuntu 14.04 LTS
My PC specs:
HP Probook
Memory 7.7 GiB
Intel® Core™ i7-5500U CPU @ 2.40GHz × 4
Intel® HD Graphics 5500 (Broadwell GT2) 
64-bit
698.4 GB

I appreciate any help anyone can give me.

Thank you,
Alyssa

---

### Post by Autodave on 2016-12-31
Since no one else has jumped in, if it were my machine, I would completely remove it and then reinstall it.

---

### Post by ajgreeny on 2016-12-31
No idea about Chrome as I have never used it, but have you tried chromium which is the open source browser on which chrome is based.

I would also rename the configuration files for chrome, which are probably in **~/.config/google-chrome** or similar, so search for that and rename it as a backup, then restart chrome to see if things are any better with the fresh profile that will be created.

---

### Post by AlyssaVS on 2016-12-31
This worked. Thank you. And Happy New Year!

---

