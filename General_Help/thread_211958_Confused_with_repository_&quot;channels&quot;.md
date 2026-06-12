---
title: "Confused with repository &quot;channels&quot;"
date: 2006-07-09
forum: General Help
---

### Post by matthias_k on 2006-07-09
Hi,

I noticed that in the synaptic repo settings, there are different "channels" for e.g. Ubuntu LTS main and Ubuntu LTS universe. However, by clicking "edit", I can set universe and multiverse for any channel, so why would I want to have a separate one for every setting I can make?

In other words, where is the difference between:

```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe

```

and

```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted universe

```
?

---

### Post by Rui Pais on 2006-07-09
hi, 

The use of one or two lines is because that way it's easy to avoid the universe repo commentig it (with #) keeping the others untouched (that in fact what synaptic do, when you activate or deactivate a repo on the gui from the menu, just add a # to the line on sources.list).

---

### Post by matthias_k on 2006-07-09
In other words, there is no difference :-)

Thanks.

---

