---
title: "block errors"
date: 2019-05-04
forum: General Help
---

### Post by Robbyx on 2019-05-04
Ubuntu 18.04

I have run badblocks and my SDD has a large number of bad blocks

When I run sudo fsck -ycfTM /dev/sda2

Wil the above repair the badblocks after it finds them? If not how do I corret them. I have tried 

Sudo badblocks -v /dev/sda1 > bad-blocks-result

I um unable to pass the fie with the bad blocks to fsck. What is the syntax?

Disks shows that the smart drive status is :OKl

---

