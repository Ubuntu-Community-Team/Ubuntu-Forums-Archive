---
title: "How to check messages on command line?"
date: 2013-02-04
forum: General Help
---

### Post by WinterMadness on 2013-02-04
Im on a server right now (through ssh, its an ubuntu server command line), and another user sent me a message apparently... I was just sitting there and it said "Message from [User here] on..."

How do I view the message?

---

### Post by CharlesA on 2013-02-04
Mail message?

You should be able to just type:

```
mail
```

---

### Post by WinterMadness on 2013-02-04
didnt work :( 

says command not found. 

its obviously not using the mail program, is there another common program for such a thing on ubuntu server?

---

### Post by tgalati4 on 2013-02-04
```
man wall
```

Perhaps it was just a wall posting.
Strange that you don't have mail installed.  It's usually installed by default.  Otherwise you won't get urgent system messages.

---

### Post by CharlesA on 2013-02-04
The only thing I can think of is wall, as tgalati4 said.

I tested it from SSH and it spit out this:

```
charles@Precise:~$ echo "test" | wall

Broadcast Message from charles@Precise
        (/dev/pts/2) at 19:18 ...

test


```

---

