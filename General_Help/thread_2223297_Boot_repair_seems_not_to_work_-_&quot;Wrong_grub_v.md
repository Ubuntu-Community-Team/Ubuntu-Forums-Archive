---
title: "Boot repair seems not to work - &quot;Wrong grub version&quot;"
date: 2014-05-10
forum: General Help
---

### Post by Lukas_Werner on 2014-05-10
Dear community,
I am about to get crazy because about 8 hours ago i started to install ubuntu as a second OS on my Notebook. After startup problems as graphical driver problems and so on it worked fine. After successfully installing it, my notebook loaded - just as expected - directly windows and did not show the grub loader. 
The advise someone given me taken i have tried boot repair... now for 3 hours and it seems not to work. Just as the OS installation here were expected problems with hibernation. After deactivating that, i get the problem "Wrong grub version detected".
I absolutely don't know what to do. Obviously i have there ubuntu as a second OS but cannot start it.

I hope so much, that you can help me. Here is the URL to the BootInfo boot repair created: [http://paste.ubuntu.com/7437395/](http://paste.ubuntu.com/7437395/)

Thanks in advance!

---

### Post by oldfred on 2014-05-10
I have seen others with the wrong grub version and 14.04, but then it seems to work.

But it looks like you used ext2? 

I cannot suggest that as it has no journal. And even in some previous versions of Ubuntu there were ext2 issues. I think with UEFI you need ext4.

But do not use any auto reinstall options. It may erase entire drive. See warning in link in my signature.

---

