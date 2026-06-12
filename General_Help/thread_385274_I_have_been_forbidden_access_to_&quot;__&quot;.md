---
title: "I have been forbidden access to &quot; / &quot;"
date: 2007-03-15
forum: General Help
---

### Post by 16777216 on 2007-03-15
I would like to know how to regain access permissions to the file system. ( The " / " folder. )

[IMG]http://lh4.google.com/image/paul16777216/RfmJmy2rS8I/AAAAAAAAAAs/13wMMTEIg2Y/snapshot2.jpg[/IMG]

This is annoying but, I am able to access all sub folders without issue.
I would change it myself but I never have been able to get a handle on numeric file permissions.

---

### Post by tszanon on 2007-03-15
I believe it should be 755:
```
sudo chmod 755 /
```

Brief explanation:
There are 3 types of access: Read, Write and eXecute (RWX), and each one has a number associated, as shown below:
```
R  W  X
4  2  1
```
Just add the numbers as you need to: all access = 4+2+1=7; except write access: 4+1=5...

In chmod, we use 3 numbers: the first is access permissions for the owner of the file; the second is for other users within the owner's group and the third number is for everyone else. So:
7 => defines that the owner has total permissions (root)
5 => defines that users within the same group of the owner can read and execute (cd /)
5 => everyone else can read and execute (you are here)

Does it solve your problem?

---

### Post by 16777216 on 2007-03-16
Thanks, I was able to fix it late last night though, I had to go the round about way to do it.

All is not lost however, your explanation of numeric file permissions has been the only on that I understand, and will serve me wonderfully. Thank you.

---

