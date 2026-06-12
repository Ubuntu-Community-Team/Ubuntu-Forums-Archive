---
title: "ulimit problem &quot;cannot modify limit&quot;"
date: 2007-10-18
forum: General Help
---

### Post by sdahlin on 2007-10-18
I am getting a problem when I try to open a session as another user (oracle in this instance).  I have gone into the /etc/security/limits.conf file and modified it with:

oracle soft nproc 2047
oracle hard nproc 16384
oracle soft nofile 1023
oracle hard nofile 65535

I have also modified the /etc/pam.d/login file with:

session required /lib/security/pam_limits.so
session required pam_limits.so

but when my .profile is run upon logging in or I enter "ulimit -u 16384" I am given the following message:

-su: ulimit: max user processes: cannot modify limit: Operation not permitted

I then tried tweaking the /etc/ssh/ssh_config file as one post indicated with:

"UsePrivilegeSeperation no"=20

This did not fix the problem.  Any suggestions?

Thanks,
Steve

---

### Post by stephdam on 2008-05-10
There are several methods to declare a shell :

If you only modify the /etc/pam.d/login, you will only modify shells spawned by the login command.

If you use ssh, then you should also modify /etc/pam.d/ssh, su also  /etc/pam.d/su and so on.

Hope this will fix your problem.

---

