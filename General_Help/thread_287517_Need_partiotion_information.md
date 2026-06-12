---
title: "Need partiotion information"
date: 2006-10-28
forum: General Help
---

### Post by badguyanil on 2006-10-28
I have a 20 gb HDD on which i want to install ubuntu. Can anyboby suggest what partitions i need to create. I had done linux installation some few  years back so dont actually remember what i had done then. I know for sure u need to create some mandatory partitions like /boot, /, and ofcouse /swap! Well i am confused! :???: Please Help!

---

### Post by ejket on 2006-10-28
If you're using the drive just for ubuntu, you can get by with just a "/swap" and a "/" (root partition).  The ordinary rule for swap is that it should be 2x your ram, though it's debatable whether a /swap larger than 500MB is useful.

I find a separate data partition handy, which I mount as /home/data ... but it's not strictly necessary.

---

### Post by hearnden on 2006-10-28
If you don't have a good reason for making separate partitions for /usr, /usr/local, /home, ..., then I'd recommend using as few partitions as possible (swap and root).  The ubuntu installer should let you do this minimum partitioning.

---

### Post by raqball on 2006-10-28
20gb?

Try this:

5gb for /
1gb swap
14gb /home

:)

---

### Post by raqball on 2006-10-28
> **ejket said:**
> The ordinary rule for swap is that it should be 2x your ram, though it's debatable whether a /swap larger than 500MB is useful.


NO the swap is just a basic emergency memory dump

---

### Post by handy on 2006-10-28
Having a separate **/home** partition is really helpful when you need to do a clean install or upgrade. Saves lots of time.

---

