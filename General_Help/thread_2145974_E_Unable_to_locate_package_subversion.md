---
title: "E: Unable to locate package subversion"
date: 2013-05-17
forum: General Help
---

### Post by IT Researcher on 2013-05-17
hi i m new to ubuntu and have installed ubuntu 13.04
i'm now trying to install svn
i tried with the codes 

sudo apt-get install subversion

but resulted in:

Building dependency tree       
Reading state information... Done
E: Unable to locate package subversion
this is the same result for oyher packages....why is this error there  and how do i overcome this

---

### Post by Elfy on 2013-05-17
Try running

```
sudo apt-get update
```

first.

If you still get issues, check the software sources are enabled correctly.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

subversion should be in main.

*Thread moved to **General Help**.*

---

### Post by IT Researcher on 2013-05-17
> **Elfy said:**
> Try running

```
sudo apt-get update
```

first.

If you still get issues, check the software sources are enabled correctly.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

subversion should be in main.

*Thread moved to **General Help**.*



tried the code .i just got


Reading package lists... Done
 even tried 


sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


any suggestion?

---

### Post by Elfy on 2013-05-17
```
apt-cache policy subversion
```

---

### Post by IT Researcher on 2013-05-17
> **Elfy said:**
> Try running

```
sudo apt-get update
```

first.

If you still get issues, check the software sources are enabled correctly.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

subversion should be in main.

*Thread moved to **General Help**.*
   

thanks a lot for the link it worked fo me

i now needed to run the code 

source LinuxX86-64Env.Set.sh


but it says bash: LinuxX86-64Env.Set.sh: No such file or directory


how can i solve this ...any suggestion
the code is used for Including  the configured environment(i configured it just prior to this step)

---

