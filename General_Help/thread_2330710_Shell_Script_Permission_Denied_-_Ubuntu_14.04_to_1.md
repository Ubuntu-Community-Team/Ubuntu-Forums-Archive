---
title: "Shell Script Permission Denied - Ubuntu 14.04 to 16.04 Upgraded"
date: 2016-07-14
forum: General Help
---

### Post by ChongMeng_Eng on 2016-07-14
I have a bash script (/usr/sbin/ejabberdctl) with properties as
"-r-xr-x--- 1 root root 14287 Jul 14 10:01 ejabberdctl" 
containing a statement to generate a uuid as below:

#!/bin/bash
...
uuid=$(uuidgen 2>/dev/null)
[ -z "$uuid" -a -f /proc/sys/kernel/random/uuid ] && uuid=$(</proc/sys/kernel/random/uuid)
....

After launched the application (ejabberd - source compiled with version 16.06+);
$ cd /var/sbin
 then issues
$ sudo ./ejabberdctl status
 will always aborted due to "permission denied" on the above two uuidgen statement. (found the root cause/reason after extensive debug)

However if I issue "$ sudo bash ./ejabberdctl status" then the script returns the correct status result i.e.
The node ejabberd@engsvr is started with status: started
ejabberd 16.07 is running in that node

Alternative if I copy the ejabberdctl to ejabberdctl_new file, then I can just issue "$ sudo ./ejabberdctl_new status" and also get the correct returned results.

=====earlier ejabberdctl script =========
Strangely the similar problem also happens with the earlier ejabberdctl script which use sh script:
#!/bin/sh 
CTL_LOCKFILE=/var/lock/ejabberdctl/ejabberdctl-1  #(example)
...
exec 8>"$CTL_LOCKFILE"
.....

The exact solution described above also applied in the case i.e. "$ sudo bash ./ejabberdctl status" or execute the duplicated file e.g. ejabberdctl_org
Note: $ "sudo sh ./ejabberdctl status" also works in this case for sh script file

============

I am not sure if the problem arises because of the Ubuntu 14.04 to 16.04 upgrading process. I do not have the problem with old script before the 16.04 upgrade.
Any help is appreciated.

---

