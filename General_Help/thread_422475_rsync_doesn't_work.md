---
title: "rsync doesn't work"
date: 2007-04-25
forum: General Help
---

### Post by tom56 on 2007-04-25
Hi all

Since upgrading to feisty rsync has stopped working. This worked fine in edgy. When I try to rsync my music to my mp3 player I get this...

rsync: chgrp failed: Operation not permitted (1)

I found another thread about this but it's in the now locked feisty development forum - [http://ubuntuforums.org/showthread.php?t=348297&highlight=rsync+chgrp](http://ubuntuforums.org/showthread.php?t=348297&highlight=rsync+chgrp)

Can anyone help?

Thanks
Tom

EDIT: Forgot to mention that this happens regardless whether I run it as myself or as root

---

### Post by mollison on 2008-06-15
I was getting the same error on trying to move files to a USB key drive. The problem was that the drive was formatted as Fat32 which does not use groups. The solution was to reformat the drive to ext3 using gparted.

Information found here:

[http://ubuntuforums.org/archive/index.php/t-472454.html](http://ubuntuforums.org/archive/index.php/t-472454.html)

---

