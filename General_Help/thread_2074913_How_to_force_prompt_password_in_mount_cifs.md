---
title: "How to force prompt password in mount cifs"
date: 2012-10-22
forum: General Help
---

### Post by ttmvtolinux on 2012-10-22
Hi,
I'm trying to mount a windows (XP) share (NTFS). My machine is 10.04LTS. The following works:
```

mount -t cifs //192.168.0.10/SQL mnt -o user=administrator,password=mypass -r

```Now I'd like to prompt for password instead of passing it as an argument to the mount command. I read the mount.cifs manual and thought that it should ask for password if I simply do not use the "password=" in the mount argument, as:
```

mount -t cifs //192.168.0.10/SQL mnt -o user=administrator -r

```But it failed. 'dmesg' says NT logon failure.
Also, 'printenv PASSWD' returns nothing.

What did I miss? Does anyone know how to make it prompt for password?

Thanks in advance.

---

### Post by lrgmmc on 2012-10-22
What type of prompt are you looking for? one in cli or in gui like the one for wifi?

---

### Post by ttmvtolinux on 2012-10-23
The commands are for Terminal. Similiar to:
```

$ ssh tt@remote
tt@remote's password:

```

---

