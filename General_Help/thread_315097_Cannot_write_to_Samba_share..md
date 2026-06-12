---
title: "Cannot write to Samba share."
date: 2006-12-08
forum: General Help
---

### Post by raid517 on 2006-12-08
Hi how do I mount a samba share and give it ful read write and execute permission in fstab?

I have a home NAS (network attached storage) router with two drives attached to it.

The NAS router is part of a workgroup called MYHOME (for example). It in turn connects to my laptop via a wireless access point (or AP).

The NAS doesn't require a password - as it is part of my workgroup - and the security for this (password WEP encryption and so on) is handled by my AP).

So I tried doing the following:

FSTAB:

```
//192.168.1.77/MYSHARE1	/mnt/Archos	smbfs	0 0
//192.168.1.77/MYSHARE2 /mnt/storage	smbfs	0 0
```

And this worked - but I cannot write to or execute anything from these shares. Again, specifically, I want to make sure I have full read, write and execute permissions on all shares.

Can anyone please tell me what I am doing wrong? Most guides I have read talk about setting the group password and UID, however I have never previously needed to do this, as I said the shares do not require a password and whenever I wanted to access a share in the past I just typed into conqueror:

```
smb://192.168.1.77/MYSHARE
```

So what exactly must I do to ensure full read write and execute permissions on these shares?

---

### Post by SyvanX on 2006-12-08
> **raid517 said:**
> 
FSTAB:

```
//192.168.1.77/MYSHARE1	/mnt/Archos	smbfs	0 0
//192.168.1.77/MYSHARE2 /mnt/storage	smbfs	0 0
```


try this for your fstab

```
//192.168.1.77/MYSHARE1	/mnt/Archos	smbfs	**defaults,rw**	0 0
//192.168.1.77/MYSHARE2 /mnt/storage	smbfs	**defaults,rw**	0 0
```

It looks like your fstab might be missing it's options.
After you edit, mount the shares

```
sudo mount /mnt/Archos
sudo mount /mnt/storage
```

---

### Post by bettlebrox on 2006-12-08
The smbfs is being mounted as root so you need to be root to access it. If your the only person using the NAS you can use the uid option in fstab to have the filesystem owned by U then you should have rwx premissions.  Alternatively, you have the fs owned by a group that you and other users, who'll use the fs, are members of that group.

I'm going to guess your the only the only one using the fs! So find your id, type id at the command-line. For example:

$id
uid=1000(zaphod) gid=1000(zaphod) groups=4(adm), ..

So my id is 1000, your's may be different. U should be able to do something like this:

//192.168.1.77/MYSHARE1	/mnt/Archos	smbfs	defaults,rwx,uid=1000	0 0
//192.168.1.77/MYSHARE2 /mnt/storage	smbfs	defaults,rw,uid=1000	0 0

Test this before you reboot! It's been a while since I've had to do this and I might have the uid in the wrong place ... ;)

---

### Post by raid517 on 2006-12-08
Thanks. That works well.

---

### Post by raid517 on 2006-12-08
Just one other thing though. How do I go about making my laptop part of the same workgroup of as my NAS?

Say my NAS is part of a workgroup called 'myhome' for example - and I have one other desktop PC which is also part of that workgroup. How would I make my laptop a member of the same workgroup as the other computers?

---

### Post by bettlebrox on 2006-12-09
Maybe this will help with joining a workgroup:

[http://ubuntuforums.org/showthread.php?t=244931](http://ubuntuforums.org/showthread.php?t=244931)

---

### Post by cybersmoker on 2007-06-01
Hey guys. I'm a noob and have tried the suggestions you have listed above and still cannot get read/write permissions.

Mounted network share to local file system. Even chmod'd the mounted folder for read write. 0777

Any help would be appreciated.

---

