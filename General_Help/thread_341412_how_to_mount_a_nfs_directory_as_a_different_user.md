---
title: "how to mount a nfs directory as a different user"
date: 2007-01-18
forum: General Help
---

### Post by mathiraj on 2007-01-18
hi,

this is my requirement. i'm logged in my ubuntu box as myself and i need to mount a remote directory as a different user. To be exact i need to use my different login name to mount that directory. I can not use the other login name in the local machine, because I connect to the remote machine via vpn.

Is there a way to specify the username/password while mounting just like in Windows?

Any idea how is this done on linux?

thanks for the responses.....
-Mathi

---

### Post by kingmonkey on 2007-01-18
Whichever machine u want to change user with do this:

log into machine as normal and open terminal and type:

```
 su you_different_user_name 
```

---

### Post by mathiraj on 2007-01-18
> **kingmonkey said:**
> Whichever machine u want to change user with do this:

log into machine as normal and open terminal and type:

```
 su you_different_user_name 
```

but the different_user_name does not exist in the local machine. It resides on the NIS server to which i connect via vpn. So, i can not do su different_user_name on the local machine.

1. i login as myself
2. su root
3. connect to my office via vpn
4. now i need to mount a NFS export directory. I need to use the different_user_name which exists on this NFS server and not on my local machine.

---

