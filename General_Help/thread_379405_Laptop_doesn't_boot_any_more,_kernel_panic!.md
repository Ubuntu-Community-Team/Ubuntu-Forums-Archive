---
title: "Laptop doesn't boot any more, kernel panic!"
date: 2007-03-08
forum: General Help
---

### Post by bjorn_swift on 2007-03-08
Woke up one morning and my laptop didn't boot. Running the "recovery mode" grub entry showed the following messages:

```

...
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
run-init: /sbin/init: Accessing a corrupted shared library
Kernel panic - not syncing: Attempted to kill init!

```

Is there any "nice" way to reinstall these shared libraries that might be corrupt? Something like apt-get install the-shared-libraries-that-might-be-needed-for-boot ;) ?

(( I suspect my laptop's hard drive to have gotten a bit flaky. It "sometimes" had trouble booting in the last two weeks or so, and then it completely broke down. ))

Cheers,
bps

---

### Post by bjorn_swift on 2007-03-08
Oh, yeah. My distribution details! I'm running 6.10 Edgy, upgraded from 6.06 Dapper. I was running linux-2.6.17-11, not that it should matter - as this happens with all other installed kernels as well.

(( Btw, when I boot the live cd and try to chroot into my installed environment, I get the same error.

```

$ mount /dev/hda3 /mnt
$ chroot /mnt /bin/bash
chroot: cannot run command: '/bin/bash': Accessing a corrupted shared library

```
))

---

### Post by anaconda on 2007-03-08
just doing filesystem check from the liveCD could fix your problem.. 

fsck -f /dev/hda3

would check the filesystem of hda3.. just remember to unmount the hda3 before running fsck..

---

### Post by bjorn_swift on 2007-03-08
Good point. Fsck -f fixed loads of issues, although the filesystem seems badly corrupted. The journal was completely wasted and once rebuilt, only a portion of my files were still there.

Sucks, but that's life. Luckily, latest backups are never more then 7 days old ;)

---

