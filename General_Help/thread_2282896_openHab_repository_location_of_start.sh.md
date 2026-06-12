---
title: "openHab repository location of start.sh"
date: 2015-06-17
forum: General Help
---

### Post by derrick1985 on 2015-06-17
Hey,

After a long hiatus from Ubuntu, i'm back on a home automation project using Arduino and openHab. I've ran into one slight problem. I want to do some testing communicating with sensors over serial, but since Ubuntu doiesn't use the same serial naming convention as it's default, you need to make a minor edit to the start.sh file to fix it. I installed openHab through the repository and not sure where the start.sh file would have gotten installed to. 

Was hoping someone could help me out with this one.  Or, at least remind me how to find a file in terminal!

Thanks!

---

### Post by tgalati4 on 2015-06-18
```
which openhab
```

and 

```
find  / -name "start.sh"
```

It could take a while.

---

