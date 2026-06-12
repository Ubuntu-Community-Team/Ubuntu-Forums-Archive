---
title: "username is not in the sudoers file. This incident will be reported"
date: 2013-02-11
forum: General Help
---

### Post by bghayad on 2013-02-11
Hi;
 
It seems some changes happened on the goup and username that caused us not able to use sudo with the username.
 
What are the commands that I have to use it if I rebooted in the recovery mode and selected the root? Can I modify the sudoers and group files manually or I have to use commands?
 
The message is:
 
saad is not in the sudoers file. This incident will be reported.
 
I rebooted in the recovery mode and selected root "Drop to root shell prompt", then I type sudo vi /etc/group and sudo vi /etc/sudoers and I found the following:
 
1) There is no admin in the group file and the following lines are existed:
 
```
root: x:0:
lpadmin: x:109:
saad: x:1000:
openerp: x:126:saad
```
 
Really, I do not know how to understand the group files ... But it seems that I have to remove saad from a group and place it in admin group, although I did not find admin but I found lpadmin.
 
2) In the sudoers file, I found the following:
 
root ALL=(ALL:ALL) ALL
 
%admin ALL=(ALL) ALL
 
%sudo ALL=(ALL:ALL) ALL
 
What are the required commands to repair?
Regards
Bilal

---

### Post by schragge on 2013-02-11
Simply add 'saad' to the group 'sudo' in */etc/group*:
```

[COLOR=green]#[/COLOR] adduser saad sudo

```

---

### Post by codemaniac on 2013-02-11
The below two pages are worth reading,

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by bghayad on 2013-02-11
I am getting the following:

root@ubuntu:/etc# sudo adduser saad sudo

Adding user 'saad' to group 'sudo' ...
Adding user saad to group sudo 
gpasswd: cannot lock /etc/group; try again later.
adduser: 'usr/bin/gpasswd -a saad sudo' returned error code1. Existing.

Any help?
Regards
Bilal

---

### Post by steeldriver on 2013-02-11
if you are doing this after dropping to a root shell from the recovery console, you will need to first remount the filesystem with read-write permissions:

```

# mount -o remount,rw /
# adduser saad sudo
```

---

### Post by schragge on 2013-02-11
First, remount the root partition read-write, then do *adduser* again. And you don't need to *sudo* when already been logged in as *root*:
```

mount -o remount,rw /
adduser saad sudo

```

**steeldriver** already beat me to it.

---

### Post by bghayad on 2013-02-12
It has been resolved by booting from recovery and selecting fsck and then selecting root and doing the above previous commands (adding the user to the sudo group).

Thanks for all.

Regards
Bilal

---

### Post by unheeding on 2013-02-12
Remember to mark this thread as solved!

---

### Post by Cheesemill on 2013-02-12
If you want to know where the incident gets reported to....

[http://xkcd.com/838/](http://xkcd.com/838/)

---

