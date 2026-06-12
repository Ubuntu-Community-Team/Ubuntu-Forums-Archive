---
title: "Can I use 2 localhost names on 1 server?"
date: 2008-05-29
forum: General Help
---

### Post by Raymond Day on 2008-05-29
Hi. I want to use 2 localhost names in one Ubuntu server. Is there a way to do that?

Like if say I like the name to be small and test so it go to the same server with both. So with samba folder with //small or //test it would go to the same place.

I guess I could have to edit the /ect/host file some way?

Would it be something like this:

127.0.0.1 localhost.localdomain localhost localhost
127.0.1.1 myubuntu.com small test

I did do that but it don't work. Any one know if there is a way to do this?

-Raymond Day

---

### Post by latna on 2008-05-29
I'm not sure I understand what you're trying to do here. Why would you want to use samba to share files - on the same computer that has access to the local filesystem?

Anyway, maybe that's not important. Maybe try putting all the hostname aliases on the same line.

```
127.0.0.1 localhost.localdomain localhost myubuntu.com small test
```

---

### Post by Raymond Day on 2008-05-29
I have a old file with a network install and all over it has a name of a old server to go to. I copied the file to my Ubuntu server but I don't want to rename it just to use this install. So it be very good if could get to the same server with 2 samba names.

It's very had to change were all the files point to on the install.

-Raymond Day

---

### Post by lotsofish on 2008-05-29
The hosts file only applies to the computer it is on. Since you are trying to connect to the Ubuntu server from a different computer, it's the other computer you are going to have to change the hosts file on. Your server is probably something like 192.168.0.100 to the other computers on the network (127.X.X.X is the local computer).

---

