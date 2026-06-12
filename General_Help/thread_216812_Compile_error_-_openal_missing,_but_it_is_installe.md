---
title: "Compile error - openal missing, but it is installed?!"
date: 2006-07-16
forum: General Help
---

### Post by viciouslime on 2006-07-16
While trying to compile warzone 2100 I get the following:
```
checking for main in -lopenal... no
checking for main in -lopenal32... no
checking for main in -lalut... no
checking OpenAL... no
configure: error: OpenAL is currently mandatory
make: *** [config.status] Error 1

```

But I have libopenal-dev installed as well as libalut-dev. Is there something else I need to install too?

---

### Post by theconley on 2006-07-20
In Fedora Core 5, I had the same problem (not with Warzone 2100).  Installing OpenAL manually fixed the problem, but I would surprised if fedora and Ubuntu both had the same packaging problems.  Let me know if that works for you.

Also, I'm looking for an OpenAL package for Dapper.  Where did you find this one?  There doesn't seem to be one on the main repository.  Is this being worked on?  Can I contribute?

~Conley

---

