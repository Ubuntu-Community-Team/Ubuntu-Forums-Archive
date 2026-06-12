---
title: "Can't install Lutris"
date: 2020-05-03
forum: General Help
---

### Post by clement-2000 on 2020-05-03
Hi experts, 
I tried to install Lutris to run a Windows only piece of software that wouldn't run with wine alone, and I ran into a major issue while trying to install which makes it impossible to install. 
I tried following the install process for Ubuntu documented here : [https://lutris.net/downloads/](https://lutris.net/downloads/) 
I just installed wine, then added the ppa, updated and intalled lutris. And when doing sudo apt-get install lutris, I got some unmet dependencies. 
Here is what I got (sorry, it's in french) : 
```

clement@clement-station:~$ sudo apt-get install lutris
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
 lutris : Dépend: python3-distro mais il n'est pas installable
          Recommande: libwine-development mais ne sera pas installé
          Recommande: winetricks mais ne sera pas installé
E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état ».

```

I also tried using -f but I got the same exact result. 

I tried searching for various solutions on the internet, but I got nothing working. I seriously don't know what to do now. 

Oh and I'm on ubuntu 16.04 if this info helps solving the problem. 

Any help would be greatly appreciated, 
Thanks in advance, 
Clément.

---

### Post by CelticWarrior on 2020-05-03
Except for the LoCo subsection this is an English only forum. French isn't a problem for me but it is for most other users here.
So, when posting any terminal output, always start the session with "LANG=C" in order to have English output.

Now, your issue...
The instructions you followed are correct but they include a PPA that doesn't support Ubuntu 16.04, only 18.04 or newer. That is, in summary, the problem you're having with the dependencies.

---

### Post by clement-2000 on 2020-05-03
Ok, thank you for your help. I'll upgrade right now (good bye cuda drivers lol). I now feel a little bit stupid, cause that's a quite basic issue in fact. 
I didn't know you could change the terminal language without messing everything up, I'll do that next time. Thanks for the tip !

---

