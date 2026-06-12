---
title: "adduser command problems"
date: 2008-02-13
forum: General Help
---

### Post by Christ_Guard on 2008-02-13
Hi guys,
    I just downloaded the newest Ubuntu, installed it, and I apereantly don't know what I typed as my user name. So, I go into recover mode and type:

```
adduser Christian admin
```

and I get the following line back:

```
The user 'Christian' does not exist.
```

I know it does not exist, thats why I am trying to add it! What is the problem here, can you help?


Thanks!

Christ_guard

---

### Post by taurus on 2008-02-13
Do you want to add another user to your system?

---

### Post by pointone on 2008-02-13
```
adduser christian
```

It will ask you what groups you want to be part of afterwards. Or:

```
adduser -G admin christian
```

```
man adduser
```

---

### Post by Christ_Guard on 2008-02-13
Thanks, but I was not added to the admin group, how do I do that?

---

