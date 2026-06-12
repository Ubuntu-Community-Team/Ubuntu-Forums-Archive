---
title: "php upgrade"
date: 2007-02-18
forum: General Help
---

### Post by lukemack on 2007-02-18
hi,

apologies if this is a duplicate - I thought I had posted this question but now can't find the post.

i would like to know how to upgrade php to 5.2.1 on an Ubuntu 6.10 install. There doesn;t seem to be a package available. I am currently on php 5.1.6.

Does this involve compiling php from source? If so, has anyone done this successfully on Ubuntu 6.10?

thanks,

lukemack.

---

### Post by xopher on 2007-02-18
There might be a fresher version of php available for feisty already, check at packages.ubuntu.com.

You could do a backport of it with prevu. (Search the forums for prevu)

---

### Post by lukemack on 2007-02-18
i couldnt find a package there - 5.1.6 seems to be the latest. are you talking about using a backport? i cant seem to find a backport for php.

any ideas where to look?

---

### Post by xopher on 2007-02-18
I was talking about making your own backport. But if it's not available there, then I guess you'd have to build it from source.

Just out of interest, what's in 5.2.1 that you need?

---

### Post by lukemack on 2007-02-18
it has a number of security updates. i am taking a class in php which recommends it. there is a feisty 5.2.0 - i think that will do. 

can you explain briefly the procedure for using a feisty package in edgy? a search on 'prevu' didnt return anything useful.

thanks,

lukemack.

---

