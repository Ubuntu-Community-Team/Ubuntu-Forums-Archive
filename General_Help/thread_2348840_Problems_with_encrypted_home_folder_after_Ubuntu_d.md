---
title: "Problems with encrypted home folder after Ubuntu doesn't boot anymore"
date: 2017-01-07
forum: General Help
---

### Post by leonlang on 2017-01-07
Hello,

After upgrading from Ubuntu 14.04 to 16.04 I couldn't log in any more. Unfortunately I didn't backup my data so now I'm trying to get access to it again. Since my home directory is encrypted, I tried to follow some instructions I found on the Internet, but it didn't work as expected.

I first tried to retrieve my passphrase, but it resulted in
```

ecryptfs-unwrap-passphrase wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-13]
Info: Check the system log for more information from libecryptfs
```

Another problem is that when I try 
```

sudo ecryptfs-recover-private
```
 the encrypted home directory is not found (even though the partition is mounted), but instead I just get 
```

INFO: Searching for encrypted private directories (this might take a while)...
find: "/run/user/999/gvfs": No permission
find: File system loop detected; "/sys/kernel/debug/pinctrl" is part of the same file system loop as "/sys/kernel/debug".
```

Do you have any ideas what I could try to solve these problems?
Thank you for helping!

Leon

Edit: We tried to fix it using an Ubuntu 16.04 Live CD

---

