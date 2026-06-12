---
title: "Strange Samba behavior"
date: 2023-03-07
forum: General Help
---

### Post by martin-colello on 2023-03-07
I am sharing a mount point from ubuntu 20.3 to Windows 10.

If I copy a file either direction it goes at 10 mbs.

If I restart smbd and then copy it goes at 100 mbs.

My smb.conf:  (all defaults, share below)

[media15]
comment = Media15
browseable = yes
path = /media15
guest ok = yes
read only = no

---

### Post by HermanAB on 2023-03-08
The apparent ‘speed’ depends on the file size vs the buffer size.  To measure the true sustained speed, you need to transfer a very large file.

---

### Post by kattrin on 2023-03-09
This often happens. Samba file sharing often has low transfer speeds, especially when copying files between different operating systems. But the fact that restarting Samba results in faster speeds suggests that there may be some configuration issues. 
Try another file transfer tool. For example, tools such as WinSCP or FileZilla use the SSH file transfer protocol, which may be faster than SMB.

---

### Post by TheFu on 2023-03-09
> **kattrin said:**
> This often happens. Samba file sharing often has low transfer speeds, especially when copying files between different operating systems. But the fact that restarting Samba results in faster speeds suggests that there may be some configuration issues. 
Try another file transfer tool. For example, tools such as WinSCP or FileZilla use the SSH file transfer protocol, which may be faster than SMB.

I haven't seen THAT much difference in performance between NFS and Samba the last 25 yrs.  Sometimes Samba is a little faster, but not always.  Generally, transfer performance is dependent on the storage performance on each side of the transfer.  If a slow SDHC flash card is uses as the source, don't expected to get much over 20 Mbps. It is the bottleneck, not the 100 Mbps network.  A 100 Mbps network would convert to about 11 MBps.  Watch the units carefully.  bits and bytes are very different sizes.  GUI programs showing speeds are usually in "MBps" whereas network tools will always show Mbps.

100 Mbps = 12.5 MBps ... add in 10-20% for samba protocol overheard and 10MBps is reasonable performance for a 100 base-TX wired connection.

**Watch the units.**

---

