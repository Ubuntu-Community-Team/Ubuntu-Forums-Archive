---
title: "Failling Hibernate"
date: 2008-04-06
forum: General Help
---

### Post by brgsousa on 2008-04-06
Hi,
I use ubuntu 7.10. When I try to hibernate the laptop, the screen goes black and then it just locks the screen. What may be happening?
Ps.: I do not have a swap partition, since the computer has 2 gigs of ram. Can that be the problem?

Thanks

---

### Post by dashnak on 2008-04-06
Yes, it is the problem...
Hibernate writes all the contents of your RAM to the SWAP, if you don't have a swap, it will simply fail.

---

### Post by brgsousa on 2008-04-06
Thanks man, I will create the partition now.

:popcorn:

---

### Post by dashnak on 2008-04-08
Great.
Now, it may or may not work just like that after you create the partition, but it would never have worked without a swap; if it still doesn't work, let me know, and I'll try to help.

---

