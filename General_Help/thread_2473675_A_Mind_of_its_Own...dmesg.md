---
title: "A Mind of its Own...dmesg"
date: 2022-04-10
forum: General Help
---

### Post by wyattwhiteeagle on 2022-04-10
My kernel has a mind of its own...


```
[    0.182574] kernel: Yama: becoming mindful.
```

A few questions...

What are the numbers at the front of the line?
Who or what is Yama?
What is meant by "becoming mindful"?

I seen this as I was skimming through /var/log/dmesg
The command I used was...

```
tac /var/log/dmesg > /home/wyatt/Desktop/Dmesg.txt
```

---

### Post by Yellow Pasque on 2022-04-10
The numbers are timestamps. In general, there are a lot of things in dmesg that you're not going to understand without googling:
[https://www.kernel.org/doc/html/latest/admin-guide/LSM/Yama.html](https://www.kernel.org/doc/html/latest/admin-guide/LSM/Yama.html)

---

