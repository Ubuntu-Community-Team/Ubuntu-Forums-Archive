---
title: "kernel error: inotify.c - what does it mean?"
date: 2008-01-01
forum: General Help
---

### Post by jure1873 on 2008-01-01
I got these strange errors in /var/log/messages today:

 [ 8418.716000] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/fs/inotify.c:172 set_dentry_child_flags()
 [ 8418.716000]  [set_dentry_child_flags+205/304] set_dentry_child_flags+0xcd/0x130
 [ 8418.716000]  [remove_watch_no_event+83/96] remove_watch_no_event+0x53/0x60
 [ 8418.716000]  [inotify_remove_watch_locked+24/80] inotify_remove_watch_locked+0x18/0x50
 [ 8418.716000]  [vfs_read+293/352] vfs_read+0x125/0x160
 [ 8418.716000]  [inotify_rm_wd+108/176] inotify_rm_wd+0x6c/0xb0
 [ 8418.716000]  [sys_inotify_rm_watch+56/96] sys_inotify_rm_watch+0x38/0x60
 [ 8418.716000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
 [ 8418.716000]  =======================
 [ 8418.716000] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/fs/inotify.c:172 set_dentry_child_flags()
 [ 8418.716000]  [set_dentry_child_flags+205/304] set_dentry_child_flags+0xcd/0x130
 [ 8418.716000]  [inotify_add_watch+245/256] inotify_add_watch+0xf5/0x100
 [ 8418.716000]  [sys_inotify_add_watch+319/352] sys_inotify_add_watch+0x13f/0x160
 [ 8418.716000]  [put_inotify_watch+52/96] put_inotify_watch+0x34/0x60
 [ 8418.716000]  [inotify_rm_wd+129/176] inotify_rm_wd+0x81/0xb0
 [ 8418.716000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
 [ 8418.716000]  =======================

what does it mean? Is there something wrong with my disks?

---

### Post by geoff123 on 2008-06-21
I just saw the same thing.  
There appears to already be a bug reported for something similar.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104837](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104837)

Anyone have any other thoughts?  For example:  

[ 1616.304901]  =======================
[ 1616.353667] WARNING: at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/fs/inotify.c:172 set_dentry_child_flags()
[ 1616.353674] Pid: 28660, comm: kded4 Tainted: P        2.6.24-19-rt #1
[ 1616.353694]  [<c01c2771>] set_dentry_child_flags+0xd1/0x160
[ 1616.353723]  [<c01c2850>] remove_watch_no_event+0x50/0x60
[ 1616.353732]  [<c01c2968>] inotify_remove_watch_locked+0x18/0x50
[ 1616.353741]  [<c0327372>] rt_mutex_lock+0x32/0x40
[ 1616.353750]  [<c01c2ccc>] inotify_rm_wd+0x6c/0xb0
[ 1616.353764]  [<c01c331b>] sys_inotify_rm_watch+0x3b/0x60
[ 1616.353775]  [<c0104592>] sysenter_past_esp+0x6b/0xa9
[ 1616.353813]  =======================
[ 1627.492908] usb 3-2: USB disconnect, address 3
[ 1644.583335] usb 3-2: new low speed USB device using uhci_hcd and address 4
[ 1644.748129] usb 3-2: configuration #1 chosen from 1 choice
[ 1644.764203] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input7

---

