---
title: "a swap partition for two operating systems"
date: 2019-03-15
forum: General Help
---

### Post by adwe on 2019-03-15
Hello I want to ask if it is possible to create a swap partition for 2 operating systems and if it is possible how would you configure it?

Thank for the support!

---

### Post by yancek on 2019-03-15
If you have a swap partition, it will be used by all of the Linux systems you have installed.

---

### Post by oldfred on 2019-03-15
New installs of Ubuntu now use swap file.
But will use swap partition if found. I have just said not to use swap partition in Something Else install and it then creates the swap file swap.

But you cannot share swap if encrypted install or if trying to hibernate. Otherwise each install will find the swap partition(s) and use them. 
Be careful that second install does not reformat swap. Of if reformatted, the first install will need to have UUID updated to the newest UUID that the reformatting did.

---

