---
title: "rtorrent+ntfs-3g?"
date: 2008-06-02
forum: General Help
---

### Post by Protoss on 2008-06-02
I just finished setting up rtorrent and a webui for it, but when I went to download my first torrent, I got an error about No Such Device. This lead me to a post saying that FUSE doesn't support **shared mmap writing** which rtorrent uses to write it's files. 

After a lot of Googleing I've been led to believe that kernel 2.6.26 will include this functionality, but I've yet to find any definitive proof besides a 6 month old patch, and a few post.
So does anyone with more kernel-esque knowledge know if 2.6.26 will include FUSE mmap writing? Cause if so, I'm definitely compiling :P

Thanks!

---

### Post by Protoss on 2008-06-04
No one knows anything about FUSE implementing shared mmap?

---

