---
title: "solitary Admin account somehow changed to Standard account (how fix?)"
date: 2014-08-31
forum: General Help
---

### Post by greg2lapa on 2014-08-31
I'm trying to solve this problem:

An Ubuntu 12.04 install had one account on it (an admin account named Jennifer). For some unknown reason this account got changed to a Standard account. I have no idea how the account got changed. The solitary user did not change it. I can't do anything from GUI because sudo asks for "root" password. I thought Ubuntu didn't create a "root" account?

when I run
    ```
id
```
I get this:  uid=1000(Jennifer) gid=1000(Jennifer) groups=1000(Jennifer)

I booted into Grub and dropped to root shell and ran
```
     useradd <new-account-name-here>
```

but I get this message:   **cannot lock /etc/passwd**

I tried running this:
```
     useradd <Jennifer> sudo
```

but nothing happens. It just returns a prompt and when I reboot I'm still a Standard user.

Any ideas how to fix this? Any ideas on why this happened in the first place?

---

### Post by steeldriver on 2014-08-31
When you booted to a recovery shell from grub, did you remember to remount the filesystem with read-write permissions?

```

mount -o remount,rw /

gpasswd --add jennifer sudo

```

---

### Post by greg2lapa on 2014-08-31
> **steeldriver said:**
> When you booted to a recovery shell from grub, did you remember to remount the filesystem with read-write permissions?

```

mount -o remount,rw /

gpasswd --add jennifer sudo

```

Thanks steeldriver.

couple questions, please?
1)  when I checked how the partitiion was being mounted there was the line:  errors=remount-ro
Is this saying to mount / as ro when user drops to root-prompt from the recovery screen?

2) I was not aware of the gpasswd command. Why didn't you use ```
usermod -G
```
Do you know where I might read more to understand the differences between usermod -G and gpasswd?

3) Any ideas how the account got changed from Admin to Standard?

Much Thanks.

---

### Post by steeldriver on 2014-08-31
1) I *think* the errors=remount-ro option in the fstab refers specifically to the situation when errors are actually detected - the ro mounting during recovery mode is just a choice made by the grub implementers

2) just personal preference - too many people get caught out by the difference between usermod's -g and -G options, so I generally steer users towards gpasswd instead. You can read about the differences in the online manual pages (man usermod / man gpasswd)

3) sorry no - basically the only way that could happen is someone removed the account from the sudo group

---

### Post by greg2lapa on 2014-08-31
> **steeldriver said:**
> 

2) just personal preference - too many people get caught out by the difference between usermod's -g and -G options, so I generally steer users towards gpasswd instead. You can read about the differences in the online manual pages (man usermod / man gpasswd)



Do I understand correctly that the equivalent of ```
gpasswd -a
```

would be ```
usermod -a -G
```

---

