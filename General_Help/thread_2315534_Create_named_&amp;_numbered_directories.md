---
title: "Create named &amp; numbered directories"
date: 2016-02-29
forum: General Help
---

### Post by mc4man on 2016-02-29
I'd like via a simple command to create x number of same named directories (except for number
So for ex. create 50 directories named rp1 thru rp50
Any ideas appreciated, no big rush

---

### Post by steeldriver on 2016-02-29
USing brace expansion

```

mkdir rp{1..50}

```

---

### Post by sudodus on 2016-02-29
```
for (( i=1;i<=50;i++ ));do echo mkdir -p rp$i;done
```

Check it with a 'dry run', then remove 'echo' :-)

---

### Post by mc4man on 2016-02-29
Excellent, both work as advertised, thanks

---

