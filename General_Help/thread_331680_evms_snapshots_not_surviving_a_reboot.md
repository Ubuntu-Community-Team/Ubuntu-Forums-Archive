---
title: "evms snapshots not surviving a reboot"
date: 2007-01-04
forum: General Help
---

### Post by LukeA on 2007-01-04
I've moved my dapper install over to a evms based setup as follows:

hda3 + sda -> LVM2 Container -> LVM2 Region -> root volume with Reiserfs

This all works fine, I can create snapshots, mount them and generally mess with them. However, the snapshots dont survive a reboot.

The main reason I moved to evms/lvm was so I could snapshot my root, boot from the snapshot and test things that may screw things up (like a dapper->edgy dist-upgrade ;)  ) 

According to the evms-announce mailing list, snapshots have been persistent since version 1.1.0-pre5 [(link)]("http://sourceforge.net/mailarchive/forum.php?forum_id=2002&max_rows=25&style=nested&viewmonth=200207")

---

