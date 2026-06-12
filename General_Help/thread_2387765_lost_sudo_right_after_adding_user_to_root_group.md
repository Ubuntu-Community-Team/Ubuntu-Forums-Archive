---
title: "lost sudo right after adding user to root group"
date: 2018-03-23
forum: General Help
---

### Post by b+atira on 2018-03-23
Hi,

Not an Ubuntu but rather general Linux question.
I had sudo rights for a user. I added the user to the root group (as a secondary group), now the user doesn't have sudo rights. (Since I didn't set an explicit password for the root user, now I don't have any access to it, so probably I'll have to reinstall my OS.)
I don't really understand, why adding a user to a group without changing any previous group memberships results in lost rights.
Any ideas?

---

### Post by steeldriver on 2018-03-23
It depends how you added the user to the group - a common gotcha is using 

```

usermod -G

```

instead of

```

usermod -aG

```

> 
       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of. Each group is
           separated from the next by a comma, with no intervening whitespace. The groups are
           subject to the same restrictions as the group given with the -g option.

[B]            If the user is currently a member of a group which is not listed, the user will be
           removed from the group.[/B] This behaviour can be changed via the -a option, which
           appends the user to the current supplementary group list.


---

### Post by b+atira on 2018-03-23
Ah, it was usermod -G
Looks like it's time for a fresh install :)
Thank you!

---

### Post by steeldriver on 2018-03-23
Since you didn't set a root password, you should be able to enter a root shell from the grub menu and add your user back to the sudo group from there - no need to reinstall

---

