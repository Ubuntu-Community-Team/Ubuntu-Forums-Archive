---
title: "No RAID disks"
date: 2007-07-01
forum: General Help
---

### Post by drukarka on 2007-07-01
Hi,

I can't install Wubi-Ubuntu on my computer :-(
"No RAID disks" during installation. Please help me. Thank you.

---

### Post by ago on 2007-07-02
> **drukarka said:**
> Hi,

I can't install Wubi-Ubuntu on my computer :-(
"No RAID disks" during installation. Please help me. Thank you.

That's not the real error. You may want to have a look inside /tmp/zenigata.log and /tmp/lupin.log
Ryun chkdisk from windows first

---

### Post by dorusone on 2007-07-02
hello

i have the same "no raid disk" message.

where can the files you mentioned be found ?
and howto get there ?

Thx
D1

---

### Post by ago on 2007-07-02
If you wait a bit you should hopefully get to a prompt where you can enter some commands. The command would be:

more /tmp/zenigata.log

Depending on the stage at which the error occurs, it might be possible to copy the logs onto the C: drive, and then zip them and attach the files here.

cp /tmp/* /media/host/

---

