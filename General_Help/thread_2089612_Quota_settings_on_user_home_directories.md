---
title: "Quota settings on user home directories"
date: 2012-11-29
forum: General Help
---

### Post by insidus on 2012-11-29
Hey,
Im trying to install some kind of "quota" for my users on my server.

Ive been messing around with quota, but i can't get it working. Im planning to sell web hosting but i need to limit the amount of space a user can have.

my file structure:

/home
/home/user1
/home/user1/usersite.co.uk

/home/user2
/home/user2/usersite.com

I need to initialize quota for /home/user1 and /home/user2.

If it helps, my /etc/fstab is:
```

proc  /proc       proc    defaults    0    0
none  /dev/pts    devpts  rw          0    0

```

[LIST]
[*]Ubuntu Server 11.04
[*]Hosted on a VPS
[/LIST]

Thanks for any help you can offer :)

---

