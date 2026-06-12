---
title: "Which files need to be copied to backup GPG?"
date: 2007-04-13
forum: General Help
---

### Post by cdrom600 on 2007-04-13
I have GnuPG running on my Ubuntu machine, and I have generated my private key.  I also have a few keys for other people which I've imported.
I know that backups are important.  I'm wondering which files I need to backup to ensure that I will not lose my private keys (and, preferably, keep a copy of all the public keys for others which I have collected).

```
$ ls ~/.gnupg
gpa.conf  pubring.gpg   random_seed  trustdb.gpg
gpg.conf  pubring.gpg~  secring.gpg
```

---

### Post by ViRMiN on 2007-04-13
pubring.gpg and secring.gpg are your public and private keyrings respectively.  Why not just keep backups of all of the files?  They're only small :)

---

### Post by cdrom600 on 2007-04-13
I just wanted to make sure that I would have the correct files in case I ever need the backups.
Thanks!

---

### Post by ViRMiN on 2007-04-13
You're welcome :)

---

### Post by meurrens on 2007-11-11
A solution is effectively to backup your whole .gnupg directory.

However if you want to make sure you can still use your keys on another system,
the standard is to save them as ascii files (.asc)
so that you can later on import them. 
(I hope you will not need to go back to Windows and be forced to do this...)

Here is how you can proceed with the 3 main frontends available on Ubuntu.

Before using them, read however the thread :
[http://ubuntuforums.org/showthread.php?t=608675&highlight=gpa](http://ubuntuforums.org/showthread.php?t=608675&highlight=gpa)
as there is a bug in the version of gpa distributed with Ubuntu.
This thread explains how to solve the problem.

With **seahorse**, 
you can backup your 2 key rings into a single zip file 
you can export a set of public keys into an .asc file 
you can NOT export your private key(s) into an .asc file (use gpa to do this) 
of course, you can import from an .asc file 

With **gpa**, 
you can NOT backup your 2 key rings into a single tar.gz or other file (use seahorse to do this) 
you can export one public key into an .asc file 
you should be able to export a set of public keys but currently there is a BUG (thus, use seahorse to do this) 
you can export (backup) one private key into an .asc file 
if you have multiple private keys, you can NOT export them all into a single .asc file (wait for a next version of gpa or seahorse ?) 
of course, you can import from an .asc file 

With **KGpg**, 
you can NOT backup your 2 key rings into a single tar.gz or other file (use seahorse to do this) 
you can export a set of public keys into an .asc file 
you can NOT export your private key(s) into an .asc file (use gpa to do this) 
of course, you can import from an .asc file

---

### Post by jis on 2008-06-02
You need at least pubring.gpg and secring.gpg, I guess. I think trustdb.gpg is good to backup, if you want to store information about which keys you trust, that is information you get in e.g. key signing parties. Can anyone confirm this?

---

### Post by jis on 2008-06-02
Does trustdb.gpg include users own key's self-signature?

---

### Post by jis on 2008-06-02
> **meurrens said:**
> 
However if you want to make sure you can still use your keys on another system,
the standard is to save them as ascii files (.asc)
so that you can later on import them. 
(I hope you will not need to go back to Windows and be forced to do this...)


If I remember right, I had no problem using pubring.gpg, secring.gpg (and trustdb.gpg) created in Windows as such in linux. What kind of experiences others have?

---

