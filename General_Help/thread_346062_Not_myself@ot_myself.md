---
title: "Not myself@ot myself"
date: 2007-01-25
forum: General Help
---

### Post by BLTicklemonster on 2007-01-25
I ran this command, 

grep <string> *.log | results.txt

and now instead of 

bill@bill-desktop:~$

I'm

bill@ill-desktop:~$

How can I get back to normal?

---

### Post by Ramses de Norre on 2007-01-25
That's strange.. Does it change when you run **bash**? 
If not: what's the output of **cat /etc/hostname**?

---

### Post by BLTicklemonster on 2007-01-25
> **Ramses de Norre said:**
> That's strange.. Does it change when you run **bash**? 
If not: what's the output of **cat /etc/hostname**?

bill@bill-desktop:~$ bash
bill@bill-desktop:~$ 


bill@bill-desktop:~$ cat /etc/hostname
bill-desktop
bill@bill-desktop:~$ 


wtf eh? it's there, it just doesn't show up. Must be the font, ya reckon?

lmao thanks for the info. I'm embarassed :redfacenewbster:

---

### Post by reclusivemonkey on 2007-01-25
You can use

```

reset

```

in your terminal if it starts to display odd things. This is handy after something like 

```

cat /dev/input/mice

```

Might be unrelated but worth knowing.

---

