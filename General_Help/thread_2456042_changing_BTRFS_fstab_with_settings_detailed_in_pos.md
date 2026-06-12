---
title: "changing BTRFS fstab with settings detailed in post result in problems ?"
date: 2021-01-03
forum: General Help
---

### Post by aug7744 on 2021-01-03
Hello.
Thanks for read my post.
I wish use BTRFS using compression and avoiding if possible useless writes on disk.
Thus I had added the settings below in fstab.

noautodefrag,compress-force=zlib:9,nospace_cache,noatime,commit=36000,max_inline=0

The settings above create problems ? If yes which problems ? the disk will has less or not useless writes and more free space ?

Avoid add :
clear_cache = Use only when happen problem with free space only being one time in each problem.
both nologreplay and norecovery break OS startup being need enter  recovery menu with read write access in partition to fix removing both  sets.

Thanks for reply.

---

