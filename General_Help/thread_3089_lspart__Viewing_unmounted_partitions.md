---
title: "lspart : Viewing unmounted partitions"
date: 2004-11-03
forum: General Help
---

### Post by mduduzi on 2004-11-03
Hi,
In the Redhat architecture systems, 'lspart' is the command to view all partitions that have been recognized -whether or not they've been mounted. The info is given like
hda1 .....
hda2....
hdb4...

etc.

How do I get such info in Ubuntu or Debian in general. Whether GUI or terminal is fine.
Thanks.

---

### Post by jdong on 2004-11-03
Why not just sfdisk -d /dev/hda ?

---

### Post by mduduzi on 2004-11-03
Problem is i have many disks and CD/DVD drives. I don't know what hd?? it is. That's just what I want to find out.
I think I asked my question incorrectly, It's thye devices that I want listed.
Thanks about sfdisk. I did not know that.

[QUOTE=jdong]Why not just sfdisk -d /dev/hda ?[/QUOTE]

---

