---
title: "large file size limit 2 GB"
date: 2006-07-27
forum: General Help
---

### Post by francesco1964 on 2006-07-27
Hi,

I'm having problems with files larger than 2 GB.

I've a file on a USB external HD with an ext3 160 GB partition, on that i've copied a disk image file with dd from another old machine with a live cd. The image is 2,4 GB.

I'm trying to copy this file to my notebook with a ext3 20 GB partition, the copy starts but when te destination reaches 2GB it stops with error.

I've tryed to copy the file from and to the 160 GB disk but this also gives the same error.

I've done some research, and it seems not to be a problem of ext3, but a problem with the block size which seems be dependent on partition size.

Anyone may help, please.

Thanks a lot.

Francesco

---

### Post by francesco1964 on 2006-09-30
Hi,

I was wrong, there is no file size limit at 2GB.

It was a corrupt file, everything goes well after a fsck.

I'm trying  to figure out how to delete my post, but don't find how to?

Does anyone knows how to delete a post?

I apologize for my wrong post.

Thanks.

Francesco

---

### Post by dcstar on 2006-09-30
> **francesco1964 said:**
> 
......
Does anyone knows how to delete a post?
......

Don't worry about it, if you want just edit your original post to something short (like "Please ignore - problem solved").

---

