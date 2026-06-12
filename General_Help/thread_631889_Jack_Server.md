---
title: "Jack Server"
date: 2007-12-04
forum: General Help
---

### Post by drutrax on 2007-12-04
i am a music producer and i have been using wine to get the applications i need but i don't want to rule out ubuntu.

but here is my question.....I used the synaptic package manager to look for the jack server and a bunch of packages appeared in the list....how do i know which of them i need?

The apps that im trying to use are all softsynths and digital audio workstations.

I've been trying out different packages for hours..so thanks in advance..

Gutsy Gibbons is the version if it matters

---

### Post by goodmanbrown on 2007-12-05
The server itself is jackd, but I think what you probably want is qjackctl.

```
sudo apt-get install qjackctl
```

It's a graphical interface to jackd, and also provides a patch bay between jack-capable applications.

Good luck!

---

