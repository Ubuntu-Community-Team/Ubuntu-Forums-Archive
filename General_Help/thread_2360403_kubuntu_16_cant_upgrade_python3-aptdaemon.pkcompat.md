---
title: "kubuntu 16 cant upgrade python3-aptdaemon.pkcompat"
date: 2017-05-04
forum: General Help
---

### Post by deathkill on 2017-05-04
couldnt upgrade python3-aptdaemon.pkcompat

so i uninstalled it and tries reinstalling but it complains it cant be installed but no reason as to why:

```
# apt install python3-aptdaemon.pkcompat
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De statusinformatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen
dat u om een onmogelijke situatie gevraagd heeft, of, indien u
de distributie 'unstable' gebruikt, dat sommige benodigde pakketten nog gemaakt moeten worden of uit 'Incoming' verwijderd werden.
De volgende informatie kan misschien helpen de situatie op te lossen:

De volgende pakketten hebben niet-voldane vereisten:
 python3-aptdaemon.pkcompat : Vereisten: python3-aptdaemon (= 1.1.1+bzr982-0ubuntu14) maar het zal niet geïnstalleerd worden
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.

```

seems this package is from a ppa i disabled.. but still looks for it in the now disabled ppa 
how can i downgrade this package to the default ubuntu 16 version?

renabled the ppa and ran 
ppa-purge ppa:kubuntu-ppa/backports

now this gives me error:
De volgende pakketten hebben niet-voldane vereisten:
 appstream : Vereisten: libappstream4 (>= 0.10.2) maar het zal niet geïnstalleerd worden

---

### Post by vasa1 on 2017-05-04
Please see your other thread here: [https://ubuntuforums.org/showthread.php?t=2360396](https://ubuntuforums.org/showthread.php?t=2360396)

---

