---
title: "Malformed line 1 in source list /etc/apt/sources.list.d/getdeb.list"
date: 2020-03-12
forum: General Help
---

### Post by bullwinkle2012 on 2020-03-12
Don't know what I did or how to correct it but I can not use sudo get-apt install. It pops up with this error.
This is installed on a laptop I repurposed.

---

### Post by SeijiSensei on 2020-03-12
Rather hard to answer the question unless we see the file.  Can you copy and paste it here inside [noparse]```

```[/noparse] tags?

---

### Post by bullwinkle2012 on 2020-03-12
deb
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb
apps

That's all I see in there

---

### Post by deadflowr on 2020-03-12
getdeb is dead, so rm the file.
```
sudo rm /etc/apt/sources.list.d/getdeb.list
```
Last I checked the domain was taken over as a spam site.

Edit: Taking a look at the site, even though it does list some software the software listed is all out-of-date (even by Ubuntu's standards)
And I don't see how you can download anything as there isn't an easy to follow guide to add the security tokens (apt's keys) and the source entries.

---

### Post by bullwinkle2012 on 2020-03-13
Thank you very much, just started learning Ubuntu so I have a ways to go.

---

