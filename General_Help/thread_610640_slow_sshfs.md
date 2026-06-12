---
title: "slow sshfs"
date: 2007-11-12
forum: General Help
---

### Post by antych on 2007-11-12
Hello,

I switched my desktop to Ubuntu. Now I need to access my devbox. I used to do that using samba shares and mounting them in windows. I wanted to do better now, I tried sshfs, I got it working but it's painfully slow. It looks few times slower than samba. 
I've never used it before so I'm not sure if this is normal. It's so slow that checking out a large codbase from svn would take hours insted of minutes. 
Is it because of the encryption? Or is there a way to speed it up?

Cheers
Karol

---

### Post by weblordpepe on 2007-11-12
What SSH server do you use in Windows?

---

### Post by tehet on 2007-11-12
> **antych said:**
> It's so slow that checking out a large codbase from svn would take hours insted of minutes. Is it because of the encryption? Or is there a way to speed it up?
The encryption makes it a bit slower and the use of FUSE probably doesn't help performance either. But if the same task now literally takes hours in stead of minutes then there's something wrong. I don't know how to trouble should this but I'd look for a sshfs.log or something like that.

If your dexbox is in the DMZ I'd use FTP for big data.

---

### Post by antych on 2007-11-12
> **weblordpepe said:**
> What SSH server do you use in Windows?

I don't use Windows anymore. I used to share between desktop window and linux devbox. Now I want to share between two linux boxes and I'm looking for better alternatives to samba.

---

### Post by antych on 2007-11-12
The performance difference measured by listing ~10k files. 
Between the same machines, I mounted one dir using samba share that I was using on windows, the other mounted using sshfs -o workaround=rename -o allow_other

time ll -R >/dev/null
mounted with samba 0.534s 
mounted with sshfs 14.784s

The difference is massive. If this is not typical for sshfs, does any one have ideas how to debug this?

---

### Post by weblordpepe on 2007-11-12
:( pass

---

