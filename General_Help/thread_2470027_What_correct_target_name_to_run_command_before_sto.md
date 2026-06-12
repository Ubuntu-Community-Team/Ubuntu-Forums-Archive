---
title: "What correct target name to run command before stopping local file system pre ?"
date: 2021-12-17
forum: General Help
---

### Post by aug7744 on 2021-12-17
Hello.
I need to run a command (writeback dmsetup flush) when OS shutdown before stopping local file system pre (mounted disk partitions) thus being possible correctly flush writeback cache.

In moment using the service below

----

[Unit]
Description=Flush
DefaultDependencies=no
Before=umount.target

[Service]
Type=oneshot
User=root
Group=root
ExecStart=/usr/local/bin/flush.sh
TimeoutStartSec=0

[Install]
WantedBy=umount.target

----

The command run before unmount.target being after stopping local-fs-pre.target when alll disk partitions are unmounted.
Shutdown.target and reboot.target not work for it.
Adding local-fs-pre.target will run the command when OS is starting not being correct.

Thanks for reply.

---

