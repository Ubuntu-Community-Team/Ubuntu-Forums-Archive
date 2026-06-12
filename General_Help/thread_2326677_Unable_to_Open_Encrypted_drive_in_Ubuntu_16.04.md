---
title: "Unable to Open Encrypted drive in Ubuntu 16.04"
date: 2016-06-03
forum: General Help
---

### Post by bizhat on 2016-06-03
I have drive encryped with cryptsetup. When i try open the drive in ubuntu, it hangs for some reason, if i enter wrong passwrord, cryptsetup able to say password is wrong, when i enter correct password, it hangs for every.

```

root@hon-pc-01:~# ps aux | grep crypt
root        53  0.0  0.0      0     0 ?        S<   20:50   0:00 [crypto]
root        73  0.0  0.0      0     0 ?        S    20:50   0:00 [ecryptfs-kthrea]
root      3045  0.0  0.2  42512 15920 ?        S<L  20:53   0:00 cryptsetup luksOpen /dev/sdc4 luks-ed0122c2-8201-4a70-b231-f52375ba7e47
root      3095  0.0  0.0      0     0 ?        S<   20:53   0:00 [kcryptd_io]
root      3096  0.0  0.0      0     0 ?        S<   20:53   0:00 [kcryptd]
root      3097  0.0  0.0      0     0 ?        S    20:53   0:00 [dmcrypt_write]
root      4129  0.0  0.0  21296   964 pts/2    S+   21:23   0:00 grep --color=auto crypt
root@hon-pc-01:~# strace -p 3045
strace: Process 3045 attached
semop(32769, [{0, 0, 0}], 1

```

dm_crypt module is loaded in kernel.


```

root@hon-pc-01:~# lsmod | grep crypt
dm_crypt               28672  1
root@hon-pc-01:~# 

```

I tried to create an encrypted file container. It created properly, but opening it  hanged for ever.

```

root@hon-pc-01:~# cryptsetup -y luksFormat /root/test1

WARNING!
========
This will overwrite data on /root/test1 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase: 
Verify passphrase: 
root@hon-pc-01:~# cryptsetup luksOpen /root/test1 volume
Enter passphrase for /root/test1: 


```

Any idea why it is not working ?

---

### Post by bizhat on 2016-06-03
The problem was because when i run cryptsetup, ubuntu suggested me to install package cryptsetup-bin, so i installed. This did not install everything needed. I got it fixed by installing package cryptsetup

```

sudo apt install cryptsetup

```

---

### Post by sinha1612 on 2016-09-16
Thanks for posting back the solution. I had the same problem and I got the answer here. :)

---

