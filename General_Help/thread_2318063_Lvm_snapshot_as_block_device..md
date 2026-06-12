---
title: "Lvm snapshot as block device."
date: 2016-03-22
forum: General Help
---

### Post by NeooeN on 2016-03-22
Hi!
I need to work on a set of data in two ways. One is in read-only mode (I need nothing more then analysis of those data), second is read-write stuff. The read-writing workflow shouldn't affect the data that are feed to the other workflow, so the simplest thing to do would be to make a full copy of my data set, but it would be a problem in the meaning of disk space required. So I came up with the idea to copy the data to a special partition placed on LVM volume and create a snapshot. Everything works kind of OK with one exception: or the snapshot (which I desired to be read-only) I need to allocate same amount of space that the origin takes to make it mountable, otherwise when I try to access /dev/volume-group/volume-file anyhow (by mount or dd) the thing reports that it is not readable at all (dd spills an error after 0 bytes, mount is compaining about zero-sized partition). Making so is not what I thought LVM works like. I desired to make a full copy of my data that would be of a very small size. So how can I achieve it with LVM?
Thanks a lot for any help!

---

