---
title: "Deleting files with '?' in their names"
date: 2007-10-02
forum: General Help
---

### Post by unprinted on 2007-10-02
I have ended up with a directory with about ten copies of a zero length file... all with the same name... and with a '?' character in the middle.

(How? Good question - a torrent had a file with an odd character in it. Clearly the bittorrent program can create such filenames, somehow, but for obvious reasons, nothing else likes them.) 

This is upsetting fsck, so it means that it won't mount on a normal boot up. As it's in my home directory partition, this is creating problems.

They're not deletable by rm *. The obvious answer would be to delete the directory, but rmdir doesn't like deleting non-empty directories.

Any other suggestions?

---

### Post by kellemes on 2007-10-02
rm -r

---

### Post by unprinted on 2007-10-02
Tried that, doesn't work:

rm cannot remove '[bad file name]': no such file or directory

---

### Post by kellemes on 2007-10-02
Does this help?
[http://www.faqs.org/faqs/unix-faq/faq/part2/section-2.html]("http://www.faqs.org/faqs/unix-faq/faq/part2/section-2.html")

---

### Post by unprinted on 2007-10-02
Ah ha - some deep breaths (as recommended!) later, yes, it does.

It was indeed created by something other than Linux and part of the problem is that it was an illegal filename under that too. Ghod knows why anything was allowed to create such a name.

Thanks.

---

