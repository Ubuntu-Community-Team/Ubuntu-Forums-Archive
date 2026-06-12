---
title: "Unable to unwrap passphrase or decrypt home directory"
date: 2015-05-31
forum: General Help
---

### Post by Ral_Jornet_Calom on 2015-05-31
I had a Kubuntu 14.04 LTS installation with my home directory encrypted. I reinstalled Kubuntu, but now I can't decrypt it.
I used the same username and password (I done it in other installations an it worked)
I didn't wrote down the passphrase, but I have the wrapped-passphrase file (/home/username/.ecryptfs/wrapped-passphrase). The problem is that when I try ```
ecryptfs-unwrap-passphrase
``` it says:

```
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
```

The user password IS CORRECT I'm sure. It is possible that is has a salt or something like that?
I tried to run ```
ecryptfs-mount-private
``` and ```
ecryptfs-recover-private
``` (same problem, incorrect password)

I don't know what to do, I'm desperate, I have college notes in there.

Thanks in advance

P.D.: Sorry for the bad english

---

### Post by mc4man on 2015-05-31
Why don't you try from a live  session, if you know the username & that user's  password then you should be able to access & copy out the files you need.
laid out here several years ago, a few things have changed but nothing significant, a recent ubuntu live session, (14.04, 15.04)  should be ok - the post with 6 & the +250
[http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory)

---

