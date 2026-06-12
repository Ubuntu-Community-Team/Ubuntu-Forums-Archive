---
title: "Devilspie configuration"
date: 2008-06-24
forum: General Help
---

### Post by lanchka on 2008-06-24
I have installed devilspie on Hardy and have file called firefox.ds that right now opens every Firefox window at a specific screen position

```
(if
(is (application_name) "Firefox")
(begin
(set_workspace 1)
(geometry "+45+0")
)
)

```

Can someone tell me how to modify this so that only browser windows open at this position whereas other windows (such as the downloads window etc,) associated with firefox open in their normal positions.

Thanks in advance,
Cheers
Bhargav

---

