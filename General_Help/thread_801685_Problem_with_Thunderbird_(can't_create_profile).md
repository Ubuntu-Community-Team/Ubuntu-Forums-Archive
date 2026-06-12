---
title: "Problem with Thunderbird (can't create profile)"
date: 2008-05-20
forum: General Help
---

### Post by Jav13r on 2008-05-20
Hello. I have the following problem: when i run thunderbird as root it works fine; but when i try to run it as user it doesn't detect no profile and its asking me to create a profile, and when i try to create a new profile i get this error: [http://img185.imageshack.us/img185/8551/screenshotdp8.png](http://img185.imageshack.us/img185/8551/screenshotdp8.png)

---

### Post by maddog39 on 2008-05-20
Looks like some simple permissions issues with your ~/.thunderbird directory. This command should fix the problem.
```

sudo chmod -Rf 0777 ~/.thunderbird

```

---

### Post by Jav13r on 2008-05-21
maddog39, that worked. problem solved. thank you!

---

