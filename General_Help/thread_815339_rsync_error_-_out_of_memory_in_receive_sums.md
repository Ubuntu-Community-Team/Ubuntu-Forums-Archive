---
title: "rsync error - out of memory in receive sums"
date: 2008-06-01
forum: General Help
---

### Post by Bruno Amaral on 2008-06-01
I have been backing up my macbook using the following command
> rsync -avz --delete --exclude '.DS_Store'  [email]username@macbook.loca[/email]l:/Users/username/ /media/file-server/backup

It used to work like a charm, but recently I started to receive the following error:

> ERROR: out of memory in receive_sums

rsync error: error allocating core memory buffers (code 22) at /SourceCache/rsync/rsync-24.1/rsync/util.c(120)

rsync: connection unexpectedly closed (6917462 bytes received so far) [receiver]

rsync error: error in rsync protocol data stream (code 12) at io.c(454) [receiver=2.6.9]

rsync: connection unexpectedly closed (2644674 bytes received so far) [generator]

rsync error: error allocating core memory buffers (code 22) at io.c(454) [generator=2.6.9]

Does anyone have a clue on how I can solve this issue?

I tried searching the forums and other sources, but so far I have had no luck.

---

