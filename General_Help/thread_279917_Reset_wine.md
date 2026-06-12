---
title: "Reset wine?"
date: 2006-10-18
forum: General Help
---

### Post by UltraSonicSite on 2006-10-18
Specifically the wine registry? I was trying to install internet explorer and added the registry file which disabled some dll's but now not even winecfg works. Where can I reset this? Or does someone have a fresh DLL list with the correct configurations?

---

### Post by Anonii on 2006-10-18
Try 

```

sudo rm -r ~/.wine && wineprefixcreate

```

**And then you will have to reinstlal your programs.**

---

### Post by UltraSonicSite on 2006-10-18
Thank you for the quick reply

i'll backup my files

---

### Post by Tanath on 2006-10-18
> **UltraSonicSite said:**
> Specifically the wine registry? I was trying to install internet explorer and added the registry file which disabled some dll's but now not even winecfg works. Where can I reset this? Or does someone have a fresh DLL list with the correct configurations?

Now why would you want to install Internet Exploder? ](*,)

---

### Post by NMUrugbysteve on 2006-11-02
> **Anonii said:**
> Try 

```

sudo rm -r ~/.wine && wineprefixcreate

```

**And then you will have to reinstlal your programs.**

DON'T USE SUDO IN YOUR HOME FOLDER.

Sorry for shouting, but there is absolutely no reason whatsoever to use sudo when dealing in your home dir.

---

### Post by aktiwers on 2007-04-11
```
rm -rf ~/.wine
```
and then
```
winecfg
```

Will reset wine too.

---

