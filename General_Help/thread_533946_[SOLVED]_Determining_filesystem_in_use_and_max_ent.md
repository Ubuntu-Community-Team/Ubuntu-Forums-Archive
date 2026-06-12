---
title: "[SOLVED] Determining filesystem in use and max entries in a directory"
date: 2007-08-24
forum: General Help
---

### Post by chris14679 on 2007-08-24
I have a VPS web server running Ubuntu Dapper and 8GB of disc space.

The nature of my project means it is necessary for me to create up to 10 million small files, each containing only around 100 bytes of data, all in the same directory. There is unfortunately no way I can subdivide them or use a database.

Is this possible, or will I come up against any limits?

How can I discover, using root SSH access, what the minimum allocation for a file on my system is, and (presumably I'll need to know this first) what format has been used for the disc?

I have heard 4k is the normal minimum allocation of space per file, can I reduce this without reformatting or reinstalling the server?

The web server is Apache2, does it have any limits on number of files it can handle in a directory? Will there be any speed implications to serve a file from a directory with that many files in it?

Thanks very much for your help!

Chris

---

### Post by apetresc on 2007-08-24
You can use ```
df -T
``` to see what each of your filesystems is formatted as. As for the minimum allocation, that's probably fs-specific right? You can check the docs for the filesystem once you discover what it is, I suppose.

I know that ext3's files-per-directory is sky-high. Way higher than 1 million.

---

### Post by chris14679 on 2007-08-24
Thanks Adrian, useful info.

I think I've actually now found a way to avoid using millions of files (I'm going to use apache's mod_redirect to fake it, and put the file contents for each file in a database)

Many thanks,
Chris

---

