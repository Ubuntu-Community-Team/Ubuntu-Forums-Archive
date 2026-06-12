---
title: "How enable dm-writecache flush when OS shutdown ?"
date: 2021-11-12
forum: General Help
---

### Post by aug7744 on 2021-11-12
I use rapiddisk cache from
[URL="https://github.com/pkoutoupis/rapiddisk"]https://github.com/pkoutoupis/rapiddisk
[/URL]Rapiddisk cache is a amazing tool.
Have created a ramdisk writeback wrapper for dm-writecache.
The writeback cache works, but when OS restart or shutdown all data cache not are flushed in disk.
dm-writecache module is loaded in kernel thus need command in kernel ? If yes is configured in grub section "linux command" ?
What command or configuration to dm-writecache flush data on OS shutdown ?

Have a nice day.

---

