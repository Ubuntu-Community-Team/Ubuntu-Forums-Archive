---
title: "ClamAV Can't execute some unpacker"
date: 2007-11-28
forum: General Help
---

### Post by MikePS on 2007-11-28
Hello fellow Ubuntu users,

I am at work right now, and I have a problem with two servers installed with the ClamAV software.
We have some Ubuntu servers, and most ClamAV's work, except for two of our servers.

When I checked the logs it said this:

```

ERROR: Can't run unrar
  ERROR: Can't execute some unpacker. Check paths and permissions on the temporary directory 

```

I tried to figure out what was wrong, even installed unrar, but it didn't help anything.
The permissions on the tmp directory are set like this: 

```

drwxrwxrwt

```

I just can't figure out what the problem is, and we really DO need a virusscanner for our servers.
Extra information: We are using Ubuntu 6.06 and 6.10.

Thanks in advance,

MikePS

---

