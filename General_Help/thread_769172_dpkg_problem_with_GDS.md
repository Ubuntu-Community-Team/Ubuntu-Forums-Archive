---
title: "dpkg problem with GDS"
date: 2008-04-26
forum: General Help
---

### Post by networkthinking on 2008-04-26
Hello,
I tried installing Google Desktop Search (GDS) some time back on my laptop and did not take.  Worked fine on the desktop but no on this laptop.

I have tried many times to remove since I can no longer download updates and such but I have limped along.  I was hoping i could upgrade to 8.04 but still cannot do this due to the GDS errors when I run any type of update.

Here is the latest thing I tried:
sudo dpkg --remove --force-remove-reinstreq google-desktop-linux

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 113911 files and directories currently installed.)
Removing google-desktop-linux ...
grep: /opt/google/desktop/.gdl_installed_files: No such file or directory
PREFIX is differ than recorded ROOT_DIR!
dpkg: error processing google-desktop-linux (--remove):
 subprocess pre-removal script returned error exit status 1
File /opt/google/desktop/.gdl_installed_files is missing!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 google-desktop-linux

Any suggestions?  Running 7.10 64

Thanks,
Wally

---

