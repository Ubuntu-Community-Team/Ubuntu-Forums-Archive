---
title: "Moving journal speed up fsck?"
date: 2013-06-12
forum: General Help
---

### Post by carboi82 on 2013-06-12
I currently have a media server using an SSD for the boot drive, and 9x2tb drives in a raid5 array. The overall performance of the array is fine, however the disk check every 30 restarts (once monthly since the server restarts daily) is horrendously slow. I realize of course part of this is due to the massive amount of data, but will moving the journal from the raid array back onto the SSD speed up this fsck? 

Also, if it will, I assume I will need to create a (max of) 400mb partition on the ssd to hold the journal file, and add the errors=panic arguement as a mount option?

---

### Post by carboi82 on 2013-06-14
*bump* 

Does anyone have any experience with this?

---

### Post by carboi82 on 2013-06-16
*shameless bump* ... anyone?

---

### Post by carboi82 on 2013-06-20
...one last *bump* I guess, then I give up?

---

