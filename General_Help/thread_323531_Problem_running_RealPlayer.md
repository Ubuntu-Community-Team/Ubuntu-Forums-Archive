---
title: "Problem running RealPlayer"
date: 2006-12-22
forum: General Help
---

### Post by maz4sag on 2006-12-22
hi, I have just downloaded RealPlayer .rpm package from the real.com. i converted this .rpm package to .deb package using alien. and installed it using dpkg. now the realplayer is installed but i dont know how to run it because it does not appear in applications. can anybody help me in this plz.

---

### Post by taurus on 2006-12-22
What happens if you run it from a terminal?

Applications -> Accessories -> Terminal
```
realplay
```

---

### Post by yopnono on 2006-12-22
> **maz4sag said:**
> hi, I have just downloaded RealPlayer .rpm package from the real.com. i converted this .rpm package to .deb package using alien. and installed it using dpkg. now the realplayer is installed but i dont know how to run it because it does not appear in applications. can anybody help me in this plz.

Better to use the .BIN from real. And there you also have the latest beta as well. 
[helixcommunity.org](helixcommunity.org)

---

### Post by maz4sag on 2006-12-22
i tried to run it from terminal but it return
mazhar@mazpc:~$ realplay
bash: realplay: command not found
mazhar@mazpc:~$

now what should i do?

---

### Post by taurus on 2006-12-22
And you're sure you did install it!!!

What's the output of this command then?

```
sudo / -name realplay* -print
```

---

### Post by sgla1 on 2007-01-07
> **taurus said:**
> And you're sure you did install it!!!

What's the output of this command then?

```
sudo / -name realplay* -print
```

I think you mean ```
sudo find / -name realplay\* -print
```
You could also use ```
locate realplay
``` or ```
which realplay
``` although the latter assumes you know the name of the executable.

Cheers,
Steve G

---

