---
title: "dd clone not working all of a sudden"
date: 2021-02-08
forum: General Help
---

### Post by rebeltaz on 2021-02-08
OK... I have done this a million times with no issues. Now all of a sudden it's not working. I have a 4gb sd card that I need to mirror to another 4gb sd card. I have always done this with dd:

```
sudo dd if=/dev/sdb of=backup-020821.img status=progress
4011180544 bytes (4.0 GB, 3.7 GiB) copied, 497 s, 8.1 MB/s 
7843840+0 records in
7843840+0 records out
4016046080 bytes (4.0 GB, 3.7 GiB) copied, 497.759 s, 8.1 MB/s
```

When I run the inverse to write that image to another card, however, it tells me that there isn't enough room:

```
sudo dd of=/dev/sdb if=backup-020821.img status=progress
3903283712 bytes (3.9 GB, 3.6 GiB) copied, 1201 s, 3.3 MB/s
dd: writing to '/dev/sdb': No space left on device
7626753+0 records in
7626752+0 records out
3904897024 bytes (3.9 GB, 3.6 GiB) copied, 1324.81 s, 2.9 MB/s
```

I have tried two target cardsm one a micro sd and the other a standard sd, and get the same result. I can write it to a larger card, but 1) that's not what I want and 2) I want to know why this isn't working all of a sudden when it always has before.

---

### Post by dinkidonk on 2021-02-09
On one card 4GB means 4GiB ( 4*(1024^3) ) and on another card it may actually mean 4GB ( 4*(1000^3) ), so you should check how many bytes the card(s) actually contains: 4GB ~= 3,7GiB. Also cheap or clone cards may not even have the advertised space.

---

