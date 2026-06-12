---
title: "System Problems"
date: 2024-06-20
forum: General Help
---

### Post by jgw on 2024-06-20
This morning I started my machine.  It connected to my network connection.  (it wouldn't do that last night).

Since I have been having a problem with 'su' I thought I would see how that was doing:
```

whoami   greg
I then went to my terminal and:
reg@greg-System-Product-Name:~$ su
Password: greg
su: Authentication failure
greg@greg-System-Product-Name:~$ su
Password: greg
su: Authentication failure

```

So, su isn't working (but sometimes it does)

then I thought I would give system-info a run and send that.  I did that, but have forgotten the address to post that file to.  Can anybody tell me where to post a large text file?

---

### Post by ajgreeny on 2024-06-20
By default Ubuntu does not make use of the ***su*** command as many other Linux distros do so what ypu are saying is exactly as it should be

Ubuntu does not make use of a root account but raises the permission level of the first user, adding that user to the **sudo** group, allowing the user to use commands prefixed with sudo, eg **sudo apt update**.  This command can not be run by a user with standard permissions; only those in the sudo group have that ability.

Having been a Ubuntu user since 2007 according to your details I can not believe that you were unaware of this way of using Ubuntu and sudo but perhaps if you have also used other distros you simply forgot this major difference between Ubuntu and those others.

To refresh your understanding of this see **RootSudo** in my signature below

---

### Post by jgw on 2024-06-20
I was showing how su didn't work when I used MY name to have it work.  This is just one of the things that should be working and are not.  I am trying to understand what is going on so I can fix it.  I should add that I could not open here for 2.5 hours this morning and then I could.  I could get in there immediately on the other machine I have here.  In other words the problem was my machine and not ubuntu forums

I am also trying to post system-info and hardinfo reports to paste.Ubuntu.com  Its been a long time since I have posted anything there.  I have one posted (system-info) at [https://paste.ubuntu.com/p/nKCPMKjDD2/](https://paste.ubuntu.com/p/nKCPMKjDD2/)  and (hardinfo report) [https://paste.ubuntu.com/p/BBDc5z3H6r/](https://paste.ubuntu.com/p/BBDc5z3H6r/)

Hope I did the right thing on the two above.

---

