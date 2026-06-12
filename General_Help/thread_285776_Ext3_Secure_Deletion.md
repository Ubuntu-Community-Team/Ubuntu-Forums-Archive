---
title: "Ext3 Secure Deletion"
date: 2006-10-27
forum: General Help
---

### Post by timhaughton on 2006-10-27
It seems that Ext3 has built in support for secure deletion. How do I set this attribute on files? Is there integration for Gnome?

p.s. I'm using Edgy

Cheers,

Tim

---

### Post by po0f on 2006-10-27
timhaughton,

Where did you read this?  Files on non-journaling filesystems can be "securely" deleted, but AFAIK you can't just delete a file and overwrite it with ones and zeroes and expect it to work on a journaling filesystem.  Data about the file still lives in the filesystem's journal.

---

### Post by flyingbrass on 2006-10-27
For an amusing read:

man wipe

---

### Post by timhaughton on 2006-10-27
> **po0f said:**
> timhaughton,

Where did you read this?  Files on non-journaling filesystems can be "securely" deleted, but AFAIK you can't just delete a file and overwrite it with ones and zeroes and expect it to work on a journaling filesystem.  Data about the file still lives in the filesystem's journal.

According to the Wikipedia entry, there is a secure-delete attribute:

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

There's also this:

[http://lwn.net/Articles/171924/](http://lwn.net/Articles/171924/)

I'm going to do some more digging to see what this secure-delete flag does. I think it might go in fstab and intercept all deletes.


Tim

---

### Post by flyingbrass on 2006-10-27
Apparently it isn't implemented.

[http://www.nabble.com/wiping-of-unused-space-on-ext3-t2231620.html](http://www.nabble.com/wiping-of-unused-space-on-ext3-t2231620.html)

As mentioned in that thread, the chattr manpage says:
> The  &#8216;c&#8217;, &#8217;s&#8217;,  and &#8216;u&#8217; attributes are not honored by the ext2 and ext3 filesystems as implemented  in  the  current  mainline  Linux  kernels. These attributes may be implemented in future versions ext2 and ext3.

---

