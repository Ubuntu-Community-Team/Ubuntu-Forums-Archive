---
title: "Ubuntu - cannot login - it blinks and shows login prompt again"
date: 2013-11-22
forum: General Help
---

### Post by guru102 on 2013-11-22
Hi everyone,

after I type my password, screen blinks and login screen is shown again in Ubuntu.

After some searching I found out that it may have to do with having some root owned files in my own directory.

Problem is that my directory is encrypted, so I cannot change owners from root shell.
I tried various solutions to mount my encrypted directory, but without success so far.

Do you have any suggestions how I can log in despite the situation, or how to mount my home directory so that I can change owners?

Thanks for any advice in forward.

---

### Post by steeldriver on 2013-11-22
Hello and welcome to the forum

Can you share (at least a rough outline) of the solutions you've already tried, and what happened (error messages and so on)? Just to save going over old ground.

---

### Post by guru102 on 2013-11-23
If you could point me to some relevant logs, I would be glad to post them here, but I didn't know myself. I only looked at auth.log and there was visible that it looped, but no error was apparent.

And what I tried:
I booted into root shell, and tried to decrypt my home folder by various methods:
- ecryptfs-recover-private as root -> this only copied the home folder without decrypting anything
- ecryptfs-mount-private after su - myself -> error that counter is locked, and that there is no file open
- sudo mount -t ecryptfs ... after su - myself -> it told me that the passphrase wasn't used, and pointed to some cache file in /root/ (I don't know why not in my home folder)

---

