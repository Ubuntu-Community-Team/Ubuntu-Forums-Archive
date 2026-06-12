---
title: "the User option in .ssh/config doesn't work"
date: 2013-11-17
forum: General Help
---

### Post by wxuyec2 on 2013-11-17
Hi everyone,

my system username is user1, the user name for 

remote server is user2. So I set 

Host ttt
HostName ttt.example.com
User user2

in my .ssh/config file.

But when I ssh ttt.example.com,

it still use user1 as the user name.

My system is Kubuntu 12.04.

any suggestion? thank you.

---

### Post by steeldriver on 2013-11-17
That's because you're invoking the server by its fully qualified name - the entries in ~/.ssh/config only apply if the name you use matches  the pattern given in the Host entry. So either execute ssh with the Host name exactly

```
ssh ttt
```

or modify the Host pattern to include the forms with and without domain portions e.g.

```

Host ttt ttt.*example* ttt.*example.com*

```

See **man ssh_config** (especially the section PATTERNS)

---

### Post by wxuyec2 on 2013-11-17
Thank you.

---

