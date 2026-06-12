---
title: "Script Execution Oddity"
date: 2015-02-06
forum: General Help
---

### Post by AlexHudghton on 2015-02-06
Ubuntu 14.04

I have 2 machines - desktop & Toshiba laptop

Both run the same Ubuntu version 14.04

I use a backup utilty on both and before I back up the systems I run a file which is on the 'Desktop' to delete stuff in the download directory and others. Then another to do the backup.

Before i upgrded to 14.04 I was on 12 and everything was fine.

Now on the desktop system, I right click the icon and get the 'run' option - select it and it works

On the laptop, I right click and no 'run' option - just 'open' and so it doesn't work. (with either file)

Permissions for the files are the same on each machine

drwxr-xr-x  2 alex alex  4096 Jan 28 12:44 .
drwxr-xr-x 45 alex alex 20480 Feb  6 09:17 ..
-rwxr-xr-x  1 alex alex    60 Jun  6  2014 delit
-rwxr-xr-x  1 root root    51 Oct 30 13:19 dirsyncpro

Any clues?

---

### Post by AlexHudghton on 2015-02-06
thanks to the 96+ people that had a look

It's fixed now

Set nautilus/preferences/behaviour to "Run executable text files when they are opened"

And now it works as expected

You really do learn something every day

---

