---
title: "wifi and conky"
date: 2014-03-06
forum: General Help
---

### Post by NyteRukh on 2014-03-06
now that i had figured out what to do with setting up conky it worked..i even put it in start up applications...tho now another problem appeared..when i rebooted the laptop, conky came on like it should, but it killed the wifi....it showed my wifi connection but said it was out of range

---

### Post by deadflowr on 2014-03-06
I don't know why conky would disable the wifi, but maybe try adding a delay to conky startup

adding the -p option to the end of the conky command will delay the launch of conky for however long you set it.
Example
```
conky -p 20
```
will delay conky from starting for 20 seconds.
See if that helps solve the wifi/conky débâcle.

---

### Post by NyteRukh on 2014-03-06
ok thanks

---

