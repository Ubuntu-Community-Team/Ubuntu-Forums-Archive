---
title: "Need name of some packages in Ubuntu"
date: 2007-04-23
forum: General Help
---

### Post by Oki on 2007-04-23
Hi

I have installed Kubuntu Feisty Fawn; and was hoping someone could tell me the name of the following package   that are in Ubuntu Feisty Fawn(want to install them): 
- chess
- sudoku
- the new program that shows the disk usage

And do you what the compiz package that are stabele are named(I guess beryl are the not so stabel of them). 

Thanks for any help :)

---

### Post by lukew on 2007-04-23
> **Oki said:**
> Hi

I have installed Kubuntu Feisty Fawn; and was hoping someone could tell me the name of the following package   that are in Ubuntu Feisty Fawn(want to install them): 
- chess
- sudoku
- the new program that shows the disk usage

And do you what the compiz package that are stabele are named(I guess beryl are the not so stabel of them). 

Thanks for any help :)

gnuchess; pouetchess brutal chess
hmmmmmmm ehhhhhh hmmmmmm brutal chess?
babou? though i like xdiskusage.

Luke

---

### Post by Sef on 2007-04-23
> I have installed Kubuntu Feisty Fawn; and was hoping someone could tell me the name of the following package that are in Ubuntu Feisty Fawn(want to install them):
- chess
- sudoku

Open Konsole and do a search for sudoku:

```
kdesu aptitude search sudoku
```

to install sudoku

```
kdesu aptitude install sudoku
```

substitue chess for sudoku to look for chess.

---

### Post by mcduck on 2007-04-23
> **Oki said:**
> Hi

- the new program that shows the disk usage

Baobab.

---

### Post by Oki on 2007-04-23
I asked since a search for "chess" gives so many different players, and I dont know the name of the one that comes with Ubuntu Feisty Fawn(and I just thought it must bee good).

Baobab gave me zero result(?).

---

### Post by mcduck on 2007-04-23
> **Oki said:**
> 
Baobab gave me zero result(?).

It seems that Baobab is not available as it's own package, but is instead included in the gnome-utils package.

---

