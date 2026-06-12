---
title: "Can't delete &quot;nonexistant&quot; files from Trash"
date: 2014-07-08
forum: General Help
---

### Post by t0p on 2014-07-08
I'm using lubuntu on an original EeePC.  I've got /home on an SD card, the rest on the 4GB(!!!) SSD.Update Manager wants to install some updates, but there isn't enough room on /. If I could empty the trash I'd have the necessary space.  But there are 3 files in the trash that I can't get rid of.  For example, there is a 135.6 MB .avi file, which the file manager is quite happy to show me in the Rubbish folder.  But if I try to delete it, I get: ```
: Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
```And there's a 104.9 MB .rar file, when I try to delete it I get```
: No such file or directory
```And a .cbz file, trying to delete which gives me```
: Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
```How do I get rid of this rubbish?

---

### Post by t0p on 2014-07-08
Oops never mind!  I should have googled before posting.  I found the solution - simply typing on command line```
cd ~/.local/share/Trash/files; rm -rf *
```Sorry for wasting anyone's time.

---

