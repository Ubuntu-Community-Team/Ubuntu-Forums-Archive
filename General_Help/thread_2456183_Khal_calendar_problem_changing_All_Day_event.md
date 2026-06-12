---
title: "Khal calendar problem changing All Day event"
date: 2021-01-06
forum: General Help
---

### Post by bill-lancaster on 2021-01-06
When trying to change the date of an all day event the event changes into a timed event with the time starting at 00:00 and ending at 00:00.
Here is an example:-
```
:~$ khal edit "all day 1"
08/01/2021-08/01/2021 all day 1
Edit?  [n]o  [q]uit  [s]ummary  [d]escription  da[t]etime range  re[p]eat  [l]ocation  [c]ategories
[a]larm  [D]elete: t
datetime range [08/01/2021 08/01/2021]: 09/01/2021 09/01/2021
Edit?  [n]o  [q]uit  [s]ummary  [d]escription  da[t]etime range  re[p]eat  [l]ocation  [c]ategories
[a]larm  [D]elete:

```

Then:-
```
:~$ khal edit "all day 1"
09/01/2021 00:00-10/01/2021 00:00 all day 1
Edit?  [n]o  [q]uit  [s]ummary  [d]escription  da[t]etime range  re[p]eat  [l]ocation  [c]ategories
[a]larm  [D]elete: 

```

At the moment  my only solution is to delete the event and re-create with the new date.

Any advice would be welcome

Kubuntu 20.04
khal, version 0.9.10

---

