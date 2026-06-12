---
title: "Need root."
date: 2008-03-29
forum: General Help
---

### Post by Petrock6 on 2008-03-29
Hey guys.
In order to install phpbb on my server, I need root, however it's ubuntu. I know the sudo password. When I tryed "adduser" it said 2 users was enough. When I did su root and put in the root password, it failed, and yes I kept trying and everything....

I can't even do the old copy  & paste files.

---

### Post by Lean 946 on 2008-03-29
Try:
```
 sudo passwd root 
```
Then type in the root password when asks.
Then:
```
 su root 
```
Or, if you dont wanto to do whats up:
```
 sudo su 
```
Bye, I expect i'd be fof any help.

---

### Post by Petrock6 on 2008-03-29
Lol, I'm a idiot. Thanks.

---

### Post by Lean 946 on 2008-03-29
In Kubuntu there is an option that says "New root console" that asks for root password and shows up a root terminal.
And im glad to be for any help (I think this is my only post)
Bye.
P.D:Anyone knows how to please mark this post as SOLVED?

---

