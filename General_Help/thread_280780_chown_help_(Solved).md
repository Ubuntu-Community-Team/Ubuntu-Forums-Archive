---
title: "chown help (Solved)"
date: 2006-10-20
forum: General Help
---

### Post by motorhead on 2006-10-20
Hi
I am trying to change ownership of my windows folder. But when I try it does this:

```

motorhead@motorhead-laptop:/home$ sudo chown motorhead:motorhead ./windows
chown: changing ownership of `./windows': Read-only file system
motorhead@motorhead-laptop:/home$ ls -l
total 12
drwxr-xr-x 13 motorhead motorhead 4096 2006-10-20 23:55 motorhead
dr-x------  1 root      root      8192 2006-10-20 06:49 windows

```

So it is not changing ownership at all. Could you please tell me what is wrong with this and how i can get this working?

Thanks in advance

---

### Post by aysiu on 2006-10-20
You can't *chown* or *chmod* Windows partitions/drives. You have to mount them with the correct parameters.

Try this guide:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by motorhead on 2006-10-20
Thank you so much, that did help.

---

