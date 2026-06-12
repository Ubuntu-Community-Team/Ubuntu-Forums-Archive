---
title: "How can I be the administrator?"
date: 2005-10-24
forum: General Help
---

### Post by daditlefsen on 2005-10-24
I am the only user of this Ubuntu but still I cant delete whatever folder I want. How can I log in to be the root?

---

### Post by darth_vector on 2005-10-24
the root account is disabled by default. use the sudo command to delete stuff that is protected

sudo rm -r /hda0

for instance (dont try that one at home :-)

if you want a root shell, type

sudo su -

if you really want to log in as root, there are plenty of threads that describe how to do so.

---

### Post by DimaIL on 2005-10-24
[QUOTE=darth_vector]if you really want to log in as root, there are plenty of threads that describe how to do so.[/QUOTE]

Can you link us to the guide? I can't find any guide.

Thanks!
Dima

---

### Post by afonic on 2005-10-24
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Please do some research before posting, this question must be the most common one in these forums! :-)

---

### Post by Xian on 2005-10-24
[QUOTE=daditlefsen]I am the only user of this Ubuntu but still I cant delete whatever folder I want. How can I log in to be the root?[/QUOTE]
You don't need to log in as root to perform this function. Besides, it is a very bad idea in the first place. Just issue the command below to open Nautilus with admin priviledges, navigate to the files you want to remove, and delete them with a right click.

```
$ sudo nautilus
```

---

### Post by darth_vector on 2005-10-24
you can enable the root account by doing a

sudo passwd root

but it is ill advised. read more about it at:

[https://wiki.ubuntu.com/RootPrivileges](https://wiki.ubuntu.com/RootPrivileges)

hope that helps

---

### Post by daditlefsen on 2005-10-24
Thanks.

---

