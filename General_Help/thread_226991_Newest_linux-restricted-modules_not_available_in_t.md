---
title: "Newest linux-restricted-modules not available in the repos"
date: 2006-08-01
forum: General Help
---

### Post by ticool on 2006-08-01
I'm searching the newest linux-restricted-modules-k7 for the 2.6.15-26 kernel. I'm still gettings the linux-restricted-modules for 2.6.15-23. Why? 
I need the newer Kernel hope to stopp some USB woes.

Searching for Kernel-upgrade howtos didn't helped me either.


Tim

---

### Post by Jucato on 2006-08-01
Check your repositories (/etc/apt/sources.list). Make sure that the dapper-security repositories has the restricted component included/enabled.

The line should look something like this:

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

---

### Post by ticool on 2006-08-01
As you see i'm gettings the older ones... so this is not my problem!
I am only able to get those for my old kernel, not for the knewer one..

---

### Post by Jucato on 2006-08-01
Well, the newest linux-restricted-modules are found in the **restricted** section of the **dapper-security** repository. If you don't have "restricted" in the dapper-security line, you won't have access to those restricted modules. that's why you're only seeing the older 2.6.15-23-k7 version, which is located in dapper (not dapper-security) only.

Here's proof: [http://packages.ubuntu.com/dapper/misc/linux-restricted-modules-2.6.15-26-k7](http://packages.ubuntu.com/dapper/misc/linux-restricted-modules-2.6.15-26-k7)
Notice the red text says "security" and "restricted"

---

### Post by ticool on 2006-08-01
DOH!  Sorry was my fault. Of Course you're right!

Thanks a lot!

---

