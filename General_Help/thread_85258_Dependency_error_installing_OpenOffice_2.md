---
title: "Dependency error installing OpenOffice 2"
date: 2005-11-02
forum: General Help
---

### Post by josir on 2005-11-02
Hi folks, 

I tried to install OO2 on Ubuntu 5.04 and I got this errors:

```

Instalando openoffice.org-base (2.0.0-4) ...
dpkg: problemas de dependência impedem configuração de openoffice.org-calc:
 openoffice.org-calc depende de libc6 (>= 2.3.5-1); porém:
  Versão de libc6 no sistema é 2.3.2.ds1-20ubuntu14.
 openoffice.org-calc depende de libgcc1 (>= 1:4.0.1); porém:
  Versão de libgcc1 no sistema é 1:4.0.0-7ubuntu6~5.04ubp1.
 openoffice.org-calc depende de libstdc++6 (>= 4.0.2); porém:
  Versão de libstdc++6 no sistema é 4.0-0pre6ubuntu7.

```

I run with dpkg -i *.deb from Brazilian Instalation ([www.openoffice.org.br](www.openoffice.org.br))

Does somebody have any tip on how to solve this problem ?

Thanks,
Josir

---

### Post by teaker1s on 2005-11-02
use synaqptic advanced search out the dependencies and install then reinstall open office

---

### Post by josir on 2005-11-05
Hi teakers, 

how do I use the synaptic advanced search ?

I entered on the synaptic manager, click on Search, make all kind of combinations (by Name, by filename, by package, etc. and I could not find "2.3.5-1" or libstdc++6

but I could not find any glue on how to install it.

Probably, it's my fault because I don't have much experience on Linux. 
So if you have a tutorial or documentation to recommend, I will appreciate.

Thanks for replying.
Josir Gomes.

---

