---
title: "Unable to resolve host"
date: 2008-06-06
forum: General Help
---

### Post by GSZX1337 on 2008-06-06
Yes, I have searched for a solution, but I think my problem lies in the fact that my etc/hostname file is messed up.

```
Black\ Mesa
```

Is all it shows.

---

### Post by Monicker on 2008-06-06
What errors are you encountering?

It may be related to an issued discussed in this sticky thread for the forum:

[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by GSZX1337 on 2008-06-06
[code="Terminal Output"]antec@Black\ Mesa:~$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo: unable to resolve host Black\ Mesa
[/code]

---

### Post by plucky on 2008-06-07
GSZX1337,


Did you see the link in **Monicker** post.

If not ```
cat/etc/hosts
cat /etc/hostname
```

Copy and paste to forum.

---

### Post by GSZX1337 on 2008-06-09
Thank you all for helping me, but I'm going to be away for about a week. I formatted the computer so I can have a clean slate. If the problem persists I will bump this thread. Thank you all again for helping.

---

