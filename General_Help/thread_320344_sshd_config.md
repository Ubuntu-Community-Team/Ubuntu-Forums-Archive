---
title: "sshd_config"
date: 2006-12-17
forum: General Help
---

### Post by Batwomansman on 2006-12-17
hi.

i want to pass on environment variables from a client to a server to execute commands on the server. 

I found this setting in sshd_config

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

this is too cryptic for me. what does that mean and how can i make sure that proper environment variables are set?

I know from other sources that

PermitUserEnvironment setting has to be set as true in /etc/ssh/sshd_config

I don't have that entry is config_sshd ...

cheers
batwomansman

---

### Post by Ramses de Norre on 2006-12-17
```
# Allow client to pass locale environment variables
AcceptEnv LANG LC_*
```
That's probably not what you're looking for, it's to set the language (= locale).

But I don't really know what you'll need to do..

---

