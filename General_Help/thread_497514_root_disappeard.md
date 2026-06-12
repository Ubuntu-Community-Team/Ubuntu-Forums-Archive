---
title: "root disappeard ?"
date: 2007-07-10
forum: General Help
---

### Post by Tex-Twil on 2007-07-10
Hello,
I dont know what I did wrong but I don't have anymore access to the root account. When I do a 
> $ sudo su
I'm asked for a password but once I write it, I return to the command line but I'm not root. 

I also realised that I have a lot of options missons in "System/Administration" menu

When I try to SSH on my PC from another one as a root I have th error:

> Permission denied, please try again.
 
What is going on ?

Thanks.

---

### Post by misconfiguration on 2007-07-10
Try su -

don't worry about using sudo to switch to SU, tell me if this works.

By default root is disabled in Ubuntu, generally you have to go to recovery mode to enable the root account. 

Enter recovery mode.

```
sudo passwd root
```

---

### Post by Tex-Twil on 2007-07-10
But the sudo su  was working without problem before.

Anyway :
> 
$ su -
Password: 
su: Authentication failure
Sorry.


---

### Post by Tex-Twil on 2007-07-11
Hi,
I found a partial solution : 

in the file /etc/sudoers was missing the entry of my group:

%my_group ALL=(ALL) ALL

I can now be root but I still have problem with the System/Administration Menu where half of the commands are missing.

---

