---
title: "ecryptfs-mount-private not working on 14.04"
date: 2014-05-22
forum: General Help
---

### Post by geordan on 2014-05-22
I can't mount my ~/Private dir on Trusty:

```
> ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [REDACTED] into the user session keyring
mount: No such file or directory
> sudo mount -t ecryptfs ~/.Private ~/Private
Unable to link the KEY_SPEC_USER_KEYRING into the KEY_SPEC_SESSION_KEYRING; there is something wrong with your kernel keyring. Did you build key retention support into your kernel?

```

For reference, I'm running, and had just done an apt-get update:
```

> uname -a
Linux anvilania 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by 10101011 on 2014-08-05
Are you sure that encryptfs is installed:

```

sudo apt-get install ecryptfs-utils

```

---

### Post by geordan on 2014-08-05
Is it possible to run ecryptfs-mount-private while ecryptfs-utils is not installed?

---

### Post by 10101011 on 2014-08-05
It probably is since I recently had a laptop without encryptfs-utils installed, but it had an encrypted home directory. However, if there was something missing, I figured perhaps encryptfs-utils would replace it.

---

### Post by geordan on 2014-08-05
Ah.  ecryptfs-utils was indeed installed.

Irritatingly, it fixed itself and is working now, and I have no idea why.

---

### Post by barrkel on 2014-12-29
It is possibly because you were trying to mount inside screen or tmux. See: [https://bugs.launchpad.net/ubuntu/+source/x2goclient/+bug/1377924](https://bugs.launchpad.net/ubuntu/+source/x2goclient/+bug/1377924)

---

