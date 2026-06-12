---
title: "fluxbox?"
date: 2007-01-03
forum: General Help
---

### Post by haxer on 2007-01-03
Hello how to install fluxbox i have ubuntu dapper with xfce :-k

---

### Post by Woodgar on 2007-01-03
Can't you just use Synaptic or aptitude -

sudo aptitude install fluxbox

I used to run Dapper and xfce and I'm pretty sure I installed fluxbox using aptitude just fine.

---

### Post by Titus A Duxass on 2007-01-03
Yes, you can use sudo aptitude install fluxbox, it will then be an option in gdm or similar.

You can also use the search facility to find this sort of information:-)

---

### Post by raul_ on 2007-01-03
Use aptitude; that way when you remove it (using aptitude) you'll remove all the dependencies as well

---

### Post by haxer on 2007-01-03
no icant do any of the alternatives synaptic doesnt see it i have all multiverse stuff and sort of that added but i cant thats why i asked :) but i dont know what the problem is..:(

---

### Post by raul_ on 2007-01-03
```

raul@osiris:~$ aptitude search fluxbox
E: /home/raul/.aptitude/config - Não foi possível abrir %s para gravação (13 Permissão negada)
p   fluxbox                         - Highly configurable and low resource X11 W

```

wrong repositories ;)

---

### Post by haxer on 2007-01-03
Hmm?:confused:

---

### Post by raul_ on 2007-01-03
Since i can find it, that means that your sources.list file is lacking some repositories. These seem to be pretty good:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

---

### Post by haxer on 2007-01-03
now it works needed to update my system then it worked proparly :P lol

---

