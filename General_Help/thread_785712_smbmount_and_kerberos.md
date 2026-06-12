---
title: "smbmount and kerberos"
date: 2008-05-07
forum: General Help
---

### Post by Chad.S on 2008-05-07
I recently installed ubuntu 8.04 and joined my computer to the domain using likewise. Everything seems to work good. I was able to add an AD group to my sudoers file so some accounts can login with sudo access, and I can access windows shares fine when logged in.

I also made a script to map a users home drive when they login to the PC. The script is using smbmount to map the share. I'm using the following syntax...

smbmount //servername/"$homedirname"$ ~/home_drive -o sec=krb5

When I try that command I get the following message...

mount error 38 = Function not implemented

A 'dmesg | tail' shows the following...

[ 3603.627226]  CIFS VFS: Kerberos negotiated but upcall support disabled!
[ 3603.627245]  CIFS VFS: Send error in SessSetup = -38
[ 3603.755753]  CIFS VFS: cifs_mount failed w/return code = -38

Does anyone know what exactly this means? Was the package not configured for krb5 support or does smbmount simply not support krb5?

When I had Gutsy installed with likewise I had no issues mounting smb shares with kerberos, so I'm kind of curious what changed.

---

### Post by Chad.S on 2008-05-08
Bump...anyone else even trying to smbmount via kerberos in Hardy?

I hate to bump threads, but I've googled this quite a bit with no luck.

---

### Post by ic3000 on 2008-06-29
Im also using likewise open and hoping to find a way to map the users home directory when a certain AD users logs in on the ubuntu PC but until now no success!

Any one can helps here!?

Thanks in advance!

---

