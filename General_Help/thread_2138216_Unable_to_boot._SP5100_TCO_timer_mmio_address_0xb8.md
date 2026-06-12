---
title: "Unable to boot. SP5100 TCO timer: mmio address 0xb8fe00 already in use"
date: 2013-04-23
forum: General Help
---

### Post by person6billion on 2013-04-23
First GRUB doesn't auto select the first boot option, and forces the user to select a boot option, but once I start booting this happens.

```
done.
Begin: Running /scripts/init-bottom ... done.
connect: No such file or directory
Please make sure that the zfs-fuse daemon is running.
internal error: failed to initialize ZFS library
fsck from util-linux 2.20.1
/dev/sdd1: clean, 422601/979200 files, 2315870/3909376 blocks
4.007525] EXT4-fs (sddl): re-mounted. Opts: errors=remount-ro
mount: Not a directory
mountall: mount /var/spool/postfix/etc/passwd [385] terminated with status 32
mountall: Filesystem could not be mounted: /var/spool/postfix/etc/passwd
mount: Not a directory
mountall: mount /var/spool/postfix/etc/shadow [388] terminated with status 32
mountall: Filesystem could not be mounted: /varispool/postfix/etc/shadow
mount: Not a directory
mountall: mount /var/spool/postfix/etc/group [390] terminated with status 32
mountall: Filesystem could not be mounted: /var/spool/postfix/etc/group
An error occurred while mounting /var/spool/postfix/etc/passwd.
mount: special device /var/run/mysqld does not exist
mountail: mount ivar/spoolipostfix/var/run/mysqld [391] terminated with status
2
mountall: Filesystem could not be mounted: /var/spool/postfix/var/run/mysqld
Press S to skip mounting or M for manual recovery
[    5.529194] SP5100 TCO timer: mmio address 0xb8fe00 already in use



```

Other instances of this issue seem to refer to some ability to interact with the system after the "mmio address already in use" error comes up but in my case nothing. I can't type in this or any other TTY. The system responds to pings and the screensaver appears to work.

---

### Post by person6billion on 2013-04-24
I realized that there is an option to skip mounting some of the directories. I tried skipping them, but it just delays the error. If anyone needs more info just ask, this is all the info that I "know" is relevant.

---

