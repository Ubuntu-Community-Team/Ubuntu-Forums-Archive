---
title: "application launch only through terminal."
date: 2013-06-02
forum: General Help
---

### Post by chinmay3 on 2013-06-02
[SIZE=3]Hello community members.):P):P

There are some applications e.g. software center , synaptic package manager which do not open through dash or launcher but when i use " sudo synaptic" it starts normally. software center launches normally but don't install any application. but if i revoked it through terminal with sudo command it can install application without any problem.[/SIZE] [SIZE=3]what shou[SIZE=3]ld i do to [SIZE=3]laun[SIZE=3]ch it normally without using sudo in terminal[SIZE=3]?

than[SIZE=3]ks i[SIZE=3]n advance.[/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by ibjsb4 on 2013-06-02
I cannot speak for the software center, I do not have it installed.  But [SIZE=2]synaptic package manager [/SIZE]should prompt you for your password when opened.  Do you get any errors when trying to open it from terminal without sudo?

```
synaptic
```

Also you should be using gksudo to launch GUI applications and not sudo.

---

### Post by chinmay3 on 2013-06-03
without sudo i get following message..

'Starting without administrative privileges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them."

---

