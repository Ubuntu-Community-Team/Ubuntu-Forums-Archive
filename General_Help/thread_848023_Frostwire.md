---
title: "Frostwire"
date: 2008-07-03
forum: General Help
---

### Post by Elena678 on 2008-07-03
Hello, do somebody how i can run frostwire

I installed frostwire, but when i klick on it, it will not start, 
I also fond an older version, but i had the same problem.

With Synaptic i found out that i was needed to install java, i also did that, but i still have the same problem. do somebody have some advice for me?

---

### Post by DarK420 on 2008-07-03
just had the same problem dude

go to add/remove programs
and search Java JRE it should be the 1st one =]

---

### Post by Elena678 on 2008-07-03
> **DarK420 said:**
> just had the same problem dude

go to add/remove programs
and search Java JRE it should be the 1st one =]

that's already installed :(

---

### Post by Tomatz on 2008-07-03
Open a terminal and type:

```
sudo update-java-alternatives --auto
```

Should work after that ;)

---

### Post by DarK420 on 2008-07-03
> **Elena678 said:**
> that's already installed :(

Hmmm,
Sun Java 6 Runtime ?

That's the one i installed then it worked perfectly

mmmm Try this

sudo update-java-alternatives -s java-6-sun

---

### Post by Elena678 on 2008-07-03
> **DarK420 said:**
> sudo update-java-alternatives -s java-6-sun

whohoo, this was working

---

