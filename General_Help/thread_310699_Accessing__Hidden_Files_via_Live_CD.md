---
title: "Accessing  Hidden Files via Live CD"
date: 2006-12-01
forum: General Help
---

### Post by babygigi on 2006-12-01
I am having a bit of trouble accessing data that is usually under hidden files. After an upgrade to Edgy from Dapper, the computer refused to log me in. After accepting the fact that i will never get back in i found out that Edgy did not support LVM partitions apparently. So by mounting my partition using a Live CD i was able to access most of my documents. Lastly i am trying to locate the .amsn file which is usually under /home/.amsn , it is usually hidden so i think that might be the reason i can not view it. but even if i turn on view hidden files i am still unable to find it. Any help will be appreciated.

Thank you in advance

---

### Post by tzulberti on 2006-12-01
If you are using nautilus as the browseer, you should press CTRL+H. If you use consele, you could use "ls -a"

---

### Post by babygigi on 2006-12-01
I have tried that, it doesn't work

---

### Post by bobosity on 2006-12-01
> **babygigi said:**
> I am having a bit of trouble accessing data that is usually under hidden files. After an upgrade to Edgy from Dapper, the computer refused to log me in. After accepting the fact that i will never get back in i found out that Edgy did not support LVM partitions apparently. So by mounting my partition using a Live CD i was able to access most of my documents. Lastly i am trying to locate the .amsn file which is usually under /home/.amsn , it is usually hidden so i think that might be the reason i can not view it. but even if i turn on view hidden files i am still unable to find it. Any help will be appreciated.

Thank you in advance
Are you sure you're looking in the right place?

/home/.amsn

might be /home/<username>/.amsn

---

### Post by babygigi on 2006-12-01
yes i am lookin in the right place, i can see all my documents that i put in my home folder as well

---

### Post by babygigi on 2006-12-01
oh i feel soo stupid, i didnt' have it under my live cd's ownership so i couldnt' see it or access it, it wasn't anything a bit of *sudo chown ubuntu* couldn't fix. Thanks anyways

---

