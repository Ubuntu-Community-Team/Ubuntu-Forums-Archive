---
title: "Repeat text in command line"
date: 2014-04-09
forum: General Help
---

### Post by elliotktm on 2014-04-09
Hi All,

I used to remember a command that repeated infinite times in the terminal.

This command was not helpful in anyway but was fun to run on a mates computer.....

E.G.

Command HA

it would then repeat HA infinite times till the break sequence.

Does anyone know the command ?

---

### Post by sudodus on 2014-04-09
```
while true; do echo 'Hello World';sleep 1;done
```

---

### Post by sisco311 on 2014-04-09
> **elliotktm said:**
> 
Does anyone know the command ?

`yes'  ;)

---

### Post by sudodus on 2014-04-09
Let's play:

0. Prepare by installing espeak

```
sudo apt-get install espeak
```

1. Let the computer laugh

```
while true; do espeak 'Haha';sleep .1;done
```

Only your fantacy will limit what is possible :-D

---

### Post by sisco311 on 2014-04-09
> **sudodus said:**
> Let's play:


m'kay, I'm in:```
espeak 'choo oo oo choo oo oo choo oo oo choo oo' & sl
```

---

### Post by Impavidus on 2014-04-09
A more elegant way:```
yes haha | espeak
```

---

### Post by sudodus on 2014-04-09
***yes***, the shorter the better :-)

Maybe this is [closer to] what the OP is looking for.

---

### Post by elliotktm on 2014-04-09
Thanks sisco311

Just what i was looking for.....

---

