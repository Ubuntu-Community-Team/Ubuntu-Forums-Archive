---
title: "One OS on two harddrives"
date: 2007-07-30
forum: General Help
---

### Post by distroman on 2007-07-30
Would a setup like this be possible?

/dev/sdb5 / 
/dev/sdb6 /home

/dev/sda2 /boot
/dev/sda6 /swap

With whatever distribution.

---

### Post by Peter76 on 2007-07-30
Sounds perfectly natural to me... That's the beauty of the unix file system... But I think it's definitely wise to have the /boot and swap partitions on the same drive, but someone please correct me if I'm wrong

---

### Post by distroman on 2007-08-01
yup that worked out fine. Thanks

---

