---
title: "external ext2 drive"
date: 2007-06-10
forum: General Help
---

### Post by glenmo on 2007-06-10
hello:

i'm on feisty and i have an external drive (usb) that i've partitioned into one fat partition and one ext2 partition.  i would prefer not to use ntfs... but whenever i plug the usb drive into my computer, it mounts as read only...

how can i tell hal to mount it as read/write?
i've tried using pysdm,  it wasn't any help, but i may be using it wrong.

this wasn't helpful enough:
[http://ubuntuforums.org/showthread.php?t=88531&highlight=hal+external+write+ext2](http://ubuntuforums.org/showthread.php?t=88531&highlight=hal+external+write+ext2)

and i've tried this:
[http://www.jennings.homelinux.net/hal.html](http://www.jennings.homelinux.net/hal.html)

although that last one seemed the most logical to me, i couldn't find how to actually set the drive to read/write... the article on the page focused on noatime option.

thank you for reading -- any help would be appreciated...

---

### Post by glenmo on 2007-06-10
actually -- i found a workaround  (one minute after posting the issue)

sudo mkdir /media/storage/data
(storage is the name of the partition)

sudo chown glenmo /media/storage/data

and now i can put whatever i want in there...

but the question remains... how would i enable whatever user that mounts the ext2 partition to write to it?

---

### Post by glenmo on 2007-06-11
so no one knows>?

this isn't a common problem?

---

