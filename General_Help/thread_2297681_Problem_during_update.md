---
title: "Problem during update"
date: 2015-10-05
forum: General Help
---

### Post by dan93 on 2015-10-05
A few weeks ago I tried updating my Mythbusters machine from a ssh  from my phone. I'm pretty sure something got messed up during that update. Now the system seems to act up randomly.I also get an error when I try to update.

I get this message when I try to update
E:*dpkg*was*interrupted,*you*must*manually*run*'sudo*dpkg*--configure*-a'*to*correct*the*problem.*

What do I do. And I'm noob so please detailed steps

Thanks

---

### Post by Bashing-om on 2015-10-05
dan93; Hello;

These things do happen; an interruption of package management operations will leave the system broke.
Activate a terminal and execute these terminal commands:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo dpkg -C

```
Which might correct the issue ->
Bearing in mind that the package manager's control files could be corrupted and that would entail replacing them. We will see if additional measures are in order.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dan93 on 2015-10-05
After running auto clean I still get theE:*dpkg*was*interrupted,*you*must*manually*run*'sudo*dpkg*--configure*-a'*to*correct*the*problem.*

---

### Post by Bashing-om on 2015-10-06
dan93; Humm ..

Try the packages manager's advise ?
```

sudo dpkg --configure -a

```

and post back the result. See then where we go.

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

