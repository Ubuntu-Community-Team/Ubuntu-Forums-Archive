---
title: "crypto_LUKS password prompt failure"
date: 2013-12-07
forum: General Help
---

### Post by helloworld1215 on 2013-12-07
RESOLVED: (wtf) Apparently you need to hold the enter for an extended period of time. 

/etc/fstab contains:

/root/e_data /root/e crypto_LUKS defaults 0 0

A password appear to be successfully prompted for, however it is impossible to enter a correct password. Here is the behavior that occurs:

1. The prompt is presented `Password:`
2. A few seconds, output from the boot from previous instructions presumably

There is no karat.
After entering the password and hitting enter nothing happens. 
When you enter another key it fails.
If you just hit enter, it fails. 

You can see an illustration of what happens in the boot.log:

> Password: /dev/sda1: 333 files, 13026/126976 clusters

crypt_activate_by_passphrase: Operation not permitted

As you can see output from previous instructions continues despite no password having been entered. I don't know if this is relevent to said failure. 

Please, please assist in getting some way to mount a container or a file system (not a partition) at boot with a password prompt. 

If you look at my other thread I am unable to get a prompt from an attempted mount of a ecryptfs at boot.

---

