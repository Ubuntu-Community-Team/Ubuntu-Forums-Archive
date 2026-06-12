---
title: "[SOLVED] ext3 partition refuses my orders"
date: 2008-04-04
forum: General Help
---

### Post by hunter_te on 2008-04-04
I recently deleted an NTFS partition by using Install CD of WinXP. Then i loaded ubuntu gutsy LIVE cd and formatted it with ext3 partition. Note that formatting the partition with ext3 hardly took 10 seconds to complete...

Pics speak louder than words....


[IMG]http://img2.freeimagehosting.net/uploads/e6809dba59.jpg[/IMG]


[IMG]http://img2.freeimagehosting.net/uploads/44f27c5ddb.jpg[/IMG]


[IMG]http://img2.freeimagehosting.net/uploads/d5111c329c.jpg[/IMG]

What to do friends? :popcorn:

---

### Post by stefangr1 on 2008-04-04
Change the ownership of /media/sda4, like:

sudo chown -R yourusername /media/sda4

---

### Post by hunter_te on 2008-04-04
What a sexy piece of command. Problem Solved. Long Live Stefangr1. Thanks a ton...YAY

---

