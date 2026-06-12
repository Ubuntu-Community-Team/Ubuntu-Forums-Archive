---
title: "File Check Kills My Laptop"
date: 2006-08-26
forum: General Help
---

### Post by noob_Lance on 2006-08-26
Hey,

Most of you know that every 30 boots ubuntu checks the file system. I have never had a problem.. until Now!

I have been using the live cd for the last 2 days since i didnt visit the mesage board to post this till now.
once the check goes and does its thing.. it returns an error saying something about a bad sector or that its already in use. is there anyway i can fix this  using the live CD and mounting my HD to solve this. thanks

~Lance

---

### Post by srunni on 2006-08-26
You could try just turning off the fsck by editing /etc/fstab. One line (the one for mounting the / filesystem) will have "0      1" instead of "0       0". If you change that last 1 to a 0, it will skip the fsck.

---

### Post by noob_Lance on 2006-08-26
thanks alot :) it worked 

but how can i defrag it or something to try and get rid of that error??

---

