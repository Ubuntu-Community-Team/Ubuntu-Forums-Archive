---
title: "Thunderbird refuses to load correct profile"
date: 2014-10-02
forum: General Help
---

### Post by Bobby_James on 2014-10-02
Hello,

For no obvious reason, TB 31.1.2 under Ubuntu 12.04 refuses to load my profile on startup. Instead, it invites me to create a new account. No folders or accounts are loaded.

My ~/.thunderbird/profile.ini folder shows:

[General]
StartWithLastProfile=0

[Profile0]
Name=Default User
IsRelative=1
Path=glvz4zpg.default
Default=1

The glvz4zpg.default folder is located under ~/.thunderbird and contains all mail and account details.

I have used from the command line thunderbird -profilemanager and played around with new accounts and suchlike without success.

However, it does load my address book and extensions (e.g. Send later). For whatever reason no folders or accounts are created.

Any suggestions? Thanks!

---

### Post by Habitual on 2014-10-02
try this in terminal and report the result:
```
cd .thunderbird
find ! -user $(whoami)
```

Please let us know,

---

