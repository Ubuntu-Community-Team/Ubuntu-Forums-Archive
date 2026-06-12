---
title: "Filesystem: XFS vs EXT3 wih data writeback mode"
date: 2007-05-10
forum: General Help
---

### Post by kilou on 2007-05-10
Hi,

there are plenty of threads and articles about Linux filesystem performances and comparison and although each filesystem has its own advantages/drawbacks depending on particular situations XFS is quite often referred as being the best performing filesystem for mixed situations and especially for large files.

However some people argue that XFS, like any other partial journalling filesystem, is not as safe as EXT3 and that after non clean power downs the data may get more easily corrupted. Now many people using EXT3 filesystem tweak it to perform better and one of the most popular tip is to enable the data=writeback mode (in fstab). This mode is faster because it caches the data (if I understood well) before writing to disk but the downside is that in case of a crash, if the cache has not been written to disk the cache's content might get lost or corrupted.

In fact the data=writeback mode of EXT3 is quite similar to what XFS does so if you use this mode in EXT3 basically you don't have any data safety benefits over using XFS. Is that right???

Therefore is it correct to say that:

- if you need a very safe filesystem you should use EXT3 with data=journal to have a complete journalling solution. It's the safest but probably the slowest (not always though...)

- if you need a fast filesystem and use EXT3 with data=writeback, you should well consider switching to XFS because XFS is as safe as EXT3 in data=writeback mode but probably faster in mixed situations!

Basically I'm using a laptop and although non clean power downs might happen they are not that frequent. I've been using EXT3 data=writeback up to now without problems but if XFS is not less safe as that I'd try to switch to XFS. 

Last question: I use Virtualbox to use XP in Ubuntu. I plan on doing a separate partition for the virtual machine. Since the virtual machine is stored in a single BIG file, will it boost performances of the virtual machine if it is stored on an XFS volume (known to best handle large files)?????

---

### Post by kilou on 2007-05-11
up

---

### Post by kilou on 2007-05-11
anybody?

---

### Post by Elle Stone on 2008-01-04
kilou asked:  Last question: I use Virtualbox to use XP in Ubuntu. I plan on doing a separate partition for the virtual machine. Since the virtual machine is stored in a single BIG file, will it boost performances of the virtual machine if it is stored on an XFS volume (known to best handle large files)?????

Same question here, except that I'm also wondering about JFS as well, for VirtualBox machines. I've looked around the internet and not found any information so far.
Elle

---

### Post by articpenguin on 2008-01-16
> **Elle Stone said:**
> kilou asked:  Last question: I use Virtualbox to use XP in Ubuntu. I plan on doing a separate partition for the virtual machine. Since the virtual machine is stored in a single BIG file, will it boost performances of the virtual machine if it is stored on an XFS volume (known to best handle large files)?????

Same question here, except that I'm also wondering about JFS as well, for VirtualBox machines. I've looked around the internet and not found any information so far.
Elle

JFS and XFS are a lot better at large files than ext3. I use JFS my filesystem because i have a lot of virtualbox images

---

