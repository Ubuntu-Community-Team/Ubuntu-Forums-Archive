---
title: "Help! Can't boot. Am on Live CD."
date: 2006-09-17
forum: General Help
---

### Post by AllanP on 2006-09-17
Shut down normally last evening. This morning I get the following:

"Halts on "checking root file system"
Contains a file system with errors, check forced
Inode 804792has illegal block(s)
UNEXPECTD INCONSISTENCY; RUN fsck MANUALLY (i.e. without -a or -p options)
fsck failed. Please repair manually ~ Reboot.
Please note that the root file system is currently mounted read-only. To remount it read-write:
# mount -n -o remount,rw /
CONTROL - D will exit from this shell and reboot
bash: lesspipe: command not found
bash: dircolors: command not found
root@ (none): ~#"

I then tried fsck with warning and now have no GRUB either.
Any way to fix this without re installing?

---

