---
title: "BTRFS sync writes"
date: 2019-09-20
forum: General Help
---

### Post by feyi19862 on 2019-09-20
[FONT=Helvetica]Hi I am not sure if this an appropriated place to ask this question. Please forgive me if the question sounds dump to you, but I have indeed did extensive googling and could not find satisfied answer.[/FONT]
[FONT=Helvetica]I would like to know how can I ensure the writes on BTRFS is always synchronized. It means the write operation returns when the filesystem has indeed committed the writes to the persistent block storage? I know in ZFS I can set the sync = always to ensure this. But on BTRFS, even though I have mounted the volume with ‘barrier’ and ‘flushoncommit’ options, the writes are still cached in the memory. I know this because the write speed is 1.9GB/s where as my block devices has a maximum throughput of 500MB/s. I found that it has something to do with delayed allocation, and on EXT4 there is option ‘nodelalloc’ to mount it without caching. However I could not find something similar for BTRFS to ensure the writes being synchronized [IMG]https://forum.rockstor.com/images/emoji/twitter/frowning.png?v=9[/IMG] Any help will be appreciated!!![/FONT]

---

### Post by #&amp;thj^% on 2019-09-20
Can you? by adding "nospace_cache" mount option.
It's been 4 years or more since I last played with BTRFS: [https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs(5)](https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs(5))
>  nospace_cache

    (nospace_cache since: 3.2, space_cache=v1 and space_cache=v2 since 4.5, default: space_cache=v1)

    Options to control the free space cache. The free space cache greatly improves performance when reading block group free space into memory. However, managing the space cache consumes some resources, including a small amount of disk space.

    There are two implementations of the free space cache. The original implementation, v1, is the safe default. The v1 space cache can be disabled at mount time with nospace_cache without clearing.

    On very large filesystems (many terabytes) and certain workloads, the performance of the v1 space cache may degrade drastically. The v2 implementation, which adds a new B-tree called the free space tree, addresses this issue. Once enabled, the v2 space cache will always be used and cannot be disabled unless it is cleared. Use clear_cache,space_cache=v1 or clear_cache,nospace_cache to do so. If v2 is enabled, kernels without v2 support will only be able to mount the filesystem in read-only mode. The btrfs(8) command currently only has read-only support for v2. A read-write command may be run on a v2 filesystem by clearing the cache, running the command, and then remounting with space_cache=v2.

    If a version is not explicitly specified, the default implementation will be chosen, which is v1 as of 4.9.
I hope I'm not misunderstanding you.

---

### Post by feyi19862 on 2019-09-20
Hi 1fallen, Thank you for the reply. I however believe that [COLOR=#000000]*space_cache is something else other than write cache. The space cache is used to accelerate the block addressing.*[/COLOR]

---

