---
title: "DVD not reconized"
date: 2006-12-06
forum: General Help
---

### Post by fjcouto on 2006-12-06
Hi there, I've done a backup at work (kubuntu 5.1) using a DVD and when I came back home (Ubuntu 6.10) I just can't open the DVD. In fact, Ubuntu doesn't even recognize the disk.
I have tried to mount it manually (sudo mount /dev/hdc) and it gives me a msg saying that I should specify the file system type (argh ... it seems like a format problem).

I have even tried to open the disk using a windows machine and again ... nothing happens (it doesn't recognize the disk).

At work, the backup DVD works fine (when I put this same DVD at work everything works fine - I can browse it, open it , run it ... everything).

I have used K3b to burn the DVD .... does anybody have any clue ???

Tks and best regards!

---

### Post by fjcouto on 2006-12-07
All right ... I'm still trying !

It seems like a mount problem:  something like system files incorrect ...

I did a dmesg | tail and the result is as follows:

[17180887.732000] attempt to access beyond end of device
[17180887.732000] hdc: rw=0, want=68, limit=4
[17180887.736000] attempt to access beyond end of device
[17180887.736000] hdc: rw=0, want=1252, limit=4
[17180887.736000] attempt to access beyond end of device
[17180887.736000] hdc: rw=0, want=1028, limit=4
[17180887.736000] UDF-fs: No partition found (1)
[17180887.752000] attempt to access beyond end of device
[17180887.752000] hdc: rw=0, want=68, limit=4
[17180887.752000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

What I don understand is why it doesn't work at home and it does work at my office. Pleasem, any help ???? How can I make it work at home ?

Best regards.

---

