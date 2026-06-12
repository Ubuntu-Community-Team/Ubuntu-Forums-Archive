---
title: "Should I convert my old vfat partitions?"
date: 2006-10-24
forum: General Help
---

### Post by glotz on 2006-10-24
Howdee!

I have two 40 gig vfat data partitions on one disk and both are at capacity (100% full). I used to run windows and that's why they're vfat. Now the question is, would I benefit somehow from coverting these partitions to some other filesystem? What benefits would other filesystems offer? How would I go about the conversion process? Would it be safe? And... would you do it? They contains some (~25) larger files (movies) and then a lot of (~40 000) smaller files (pictures) among other things. I'm on an older puter if that plays a role here.

Thanks for any insight and help!

ps. to any hollywood agents: they're all 200% legal, of course! :mrgreen:

---

### Post by mssever on 2006-10-24
Changing the type will require you to backup and reformat. ext3 is more native to Linux (permissions work right, etc.) and it supports files larger than 4 GB.

Personally, I use ext3 wherever possible. You might want to compare reiserfs with ext3. I don't know much about reiserfs, but some people really like it.

---

### Post by glotz on 2006-10-24
Ah, I was hoping to avoid the reformat racket... I guess I'll be visiting the shop then when I will convert. Would the ext3 have other advances besides the permissions (and the rather large files)? Would it be faster? Would it have more space or something? (again, it's my data that's there, my / is obviously ext3)

I found this [http://tzukanov.narod.ru/convertfs/](http://tzukanov.narod.ru/convertfs/) but I don't feel like gambling with my data. EDIT: looks like it was in the debian unstable repos but is going bye bye [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=386967](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=386967)

---

### Post by mssever on 2006-10-24
My biggest complaint with vfat is the file size limit. But also, ext3 doesn't get fragmented nearly so much (if fact, most people never defrag ext3 partitons). Also, ext3 is journalling, which means that your data is safer in a system crash. NTFS does this, too, but NTFS has other problems working with Linux.

---

### Post by glotz on 2006-10-24
I see. Thanks for the advice!

---

