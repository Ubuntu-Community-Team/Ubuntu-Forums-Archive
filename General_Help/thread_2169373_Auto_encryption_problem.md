---
title: "Auto encryption problem"
date: 2013-08-21
forum: General Help
---

### Post by Clarkey252 on 2013-08-21
I'm running Ubuntu server 12.04.2 and just had to restart it. Once I did then my home area auto-encrypted itself.

I have read the readme and it states to run ```
ecryptfs-mount-private
```

When I do I get the following:
```
clarkey252@SERVER:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [xxx] into the user session keyring
mount: Operation not permitted

```

So thinking it's not permitting me means I need to sudo:
```
clarkey252@SERVER:~$ sudo ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [xxx] into the user session keyring
fopen: No such file or directory

```

Please help!
Thanks,
Clarkey252.

---

### Post by reyals140 on 2013-08-29
Bump
Same issue.

---

