---
title: "Creating a large file?"
date: 2006-07-20
forum: General Help
---

### Post by dharrigan on 2006-07-20
Hi,

Does Ubuntu have the equivalent of mkfile? I want to be able to create a large file of arbitary size using one command.

dd if=/dev/random of=randata bs=1000

is far too slow (and depends somewhat on userinput). Say I want to make a file of 1GB in size, I would love to run a command such as:

mkfile data.txt 1GB (or 1024MB)

Thanks!

-=david=-

---

### Post by JoshHendo on 2006-07-20
-edit, woops, ment to post somewhere else >.<. I hate it when that happens-

---

### Post by krivosh on 2007-01-11
Hi,
/dev/random is incredibly slow, you're right ](*,)  ... anyway, if you don't care about the content, /dev/zero is pretty fast to supplement it :evil:

---

