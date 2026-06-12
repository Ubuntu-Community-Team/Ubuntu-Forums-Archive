---
title: "TaskCoach"
date: 2019-04-19
forum: General Help
---

### Post by yoramdavid on 2019-04-19
Hello all,
I have TaskCoach installed, there was an update recently and since then I cannot launch the app anymore.

From the command line:
[HTML]taskcoach

Command 'taskcoach' not found, but can be installed with:

sudo apt install taskcoach
[/HTML]

Then:
[HTML]sudo apt install taskcoach
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
taskcoach is already the newest version (1.4.5-0ubuntu18~bionic-1).
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 117 não actualizados.[/HTML]
I already purge and reinstalled it, still nothing.

Any suggestions?

Thank you.
David

---

### Post by AlbertoDAU on 2019-10-05
I am having the same problem... tried to install several times from ubuntu repository and ppa, but nothing... From I have read this was solved for version 19.10, but 18.04 seems to be left out...

---

### Post by AlbertoDAU on 2019-10-05
I believe I have found a solution, instead of running the command "taskcoach", you should run "taskcoach.py" For some reason the menu shortcut calls it without the "py" it calls "taskcoach %f". It worked for me on xubuntu 18.04.1

---

