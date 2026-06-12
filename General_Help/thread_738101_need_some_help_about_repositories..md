---
title: "need some help about repositories."
date: 2008-03-28
forum: General Help
---

### Post by haha123 on 2008-03-28
hello everyone.I selected "all opensource applications" in add/remove programs.I observed that th number of programs in the list is not increasing when i am reloading the repositories also...is there anything that there are constant number of programs???
 and can we increase thet number by by adding third party sources..if we can any body please give me some of the sources addresses...thanks in advance.

---

### Post by justleen on 2008-03-28
never noticed / paid attention to that, really..

i got main, multi and universe and restricted checked, wich gives me 23132 packages...

you could check it by unchecking everything but main, reload an see if there is a difference i suppose.. (cant test it from here.. behind a firewall)

---

### Post by Oldsoldier2003 on 2008-03-28
double posted

---

### Post by Oldsoldier2003 on 2008-03-28
System>Administration>Software Source

turn on the first four repos then add any third party repos on the second tab,
```
sudo apt-get update
```

---

### Post by justleen on 2008-03-28
> **Oldsoldier2003 said:**
> ```
sudo apt-get update
```


the OP did mention after reloading...

---

### Post by Oldsoldier2003 on 2008-03-28
> **justleen said:**
> the OP did mention after reloading...

yeah i pressed post before i was actuall finished and even managed to double post while fixing it.

---

