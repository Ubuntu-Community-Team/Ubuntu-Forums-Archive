---
title: "Replacement of Exceed by Hummingbird ?"
date: 2007-01-17
forum: General Help
---

### Post by snowboard975 on 2007-01-17
Hi there,
I used Exceed by Hummingbird to run a xprogram on a Redhat server of the lab of the university.
I thought that I would not need Exceed if I use a linux OS to connect to the server so I installed ubuntu on my computer.
But when I tried to run the xprogram on the server of school, I faced some errors.

I used the following method:

I opened the Application>Accessories>Terminal
```

$ telnet 123.123.123.123              // 123.123.123.123 is the ip address of the server

```
and loged on using my id and password.
But when I tried to run the xprogram by
```

$ icfb                                     // icfb is a xprogram on the server of the university that I wanted to use on the server of the university

```

it showed up the following errors.
```

*ERROR* X Window Display Initialization failure
*WARNING* X Window Display Initialization failure

```
How can I run the icfb program on the school server as I did before in windows xp using Exceed by Hummingbird?

---

### Post by snowboard975 on 2007-02-20
```
ssh -X *ipaddress*
```
solved my problem...

---

