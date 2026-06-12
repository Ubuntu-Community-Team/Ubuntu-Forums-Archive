---
title: "How to force SSH (Ubuntu 20.04) to always demand a passphrase for the identity file?"
date: 2021-08-20
forum: General Help
---

### Post by johnjones1234 on 2021-08-20
Is there a way to demand that SSH always requests a password when using an identity file?    For example, ssh -i /path/to/file user@ip_address will demand a passphrase the for first login. However, the phrase is then cached and it won't request again.

---

### Post by TheFu on 2021-08-21
Is ssh-agent running?  If it is, how is that configured?

The manpage says this:
```
     -t life
             Set a default value for the maximum lifetime of identities added to the
             agent.  The lifetime may be specified in seconds or in a time format speci&#8208;
             fied in sshd_config(5).  A lifetime specified for an identity with
             ssh-add(1) overrides this value.  Without this option the default maximum
             lifetime is forever.
```

---

