---
title: "how to go to the home folder in an encrypted home folder."
date: 2012-12-09
forum: General Help
---

### Post by johnycsf on 2012-12-09
Hello all. I am still somewhat new to linux.

I dual boot backtrack 5 R3 and ubuntu 13.04.
During the installation of ubuntu I chose to encrypt the home folder now whenever I boot backtrack and I need a file that's on Documents or any folder of the Home Folder of the ubuntu partition it won't let me and I don't know how to fix that!!

Thanks!

---

### Post by Kirk Schnable on 2012-12-09
> **johnycsf said:**
> Hello all. I am still somewhat new to linux.

I dual boot backtrack 5 R3 and ubuntu 13.04.
During the installation of ubuntu I chose to encrypt the home folder now whenever I boot backtrack and I need a file that's on Documents or any folder of the Home Folder of the ubuntu partition it won't let me and I don't know how to fix that!!

Thanks!

The Ubuntu Community Documentation appears to be having server problems at the moment, but upon its return, you may find these useful.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

As far as I know, the encrypted home folder is just a standard ecryptfs, and can be mounted the same way. 

[http://manpages.ubuntu.com/manpages/precise/man1/ecryptfs-mount-private.1.html](http://manpages.ubuntu.com/manpages/precise/man1/ecryptfs-mount-private.1.html)

---

### Post by johnycsf on 2012-12-09
I put the screenshot of what happens and I don't know how to mount it.
I read the articles on the links you sent me but I am still unable to access my home folder that is encrypted on a separate partition.[ATTACH]228413[/ATTACH]

[ATTACH]228418[/ATTACH]

---

