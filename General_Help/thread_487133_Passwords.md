---
title: "Passwords"
date: 2007-06-28
forum: General Help
---

### Post by mouseboyx on 2007-06-28
Is it possible to make it so I don't need to type in my stupid password every time i open an administrative app? or do anything involving being root?

---

### Post by tgm4883 on 2007-06-28
> **mouseboyx said:**
> Is it possible to make it so I don't need to type in my stupid password every time i open an administrative app? or do anything involving being root?

Yea, but its a very bad idea

---

### Post by chrisccoulson on 2007-06-28
^^^Yes, what tgm4883 said. You don't get any notification then if you try to do anything requiring root privileges. Not a good idea.

However, if you must - in a terminal:

```
sudo visudo
```

Edit the line that reads

```
%admin  ALL=(ALL) ALL
```

to read

```
%admin  ALL=NOPASSWD: ALL
```

Why would you want to do this though? I rarely have to enter my password on my machine during normal day-to-day use.

---

### Post by tgm4883 on 2007-06-28
> **chrisccoulson said:**
> In a terminal:

```
sudo visudo
```

Edit the line that reads

```
%admin  ALL=(ALL) ALL
```

to read

```
%admin  ALL=NOPASSWD: ALL
```

Why would you want to do this though? I rarely have to enter my password on my machine during normal day-to-day use.

Although doing this would be a big security risk

---

### Post by chrisccoulson on 2007-06-28
I agree. Just edited my post to re-iterate this

---

### Post by bodhi.zazen on 2007-06-28
> **mouseboyx said:**
> Is it possible to make it so I don't need to type in my stupid password every time i open an administrative app? or do anything involving being root?

Best to : ```
sudo -i
```

do your admin work

log out

---

### Post by mouseboyx on 2007-06-28
Thanks, for the info and the warnings but i do not like being prompted for anything. I want it it just work.

---

### Post by tgm4883 on 2007-06-28
> **mouseboyx said:**
> Thanks, for the info and the warnings but i do not like being prompted for anything. I want it it just work.

Ok, but I don't even think it's a security risk.  When you leave your system that wide open I thinks it's more security non existant

---

