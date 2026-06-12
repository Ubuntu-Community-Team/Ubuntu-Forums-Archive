---
title: "Remove dejavu fonts."
date: 2019-02-25
forum: General Help
---

### Post by Furycd001 on 2019-02-25
HI.. Is it possible to remove / uninstall dejavu fonts from an xubuntu system without having to reinstall xubuntu-core & xubuntu-desktop ?? If so how can it be done ?? Thanks in advance for any help or replies....

---

### Post by Holger_Gehrke on 2019-02-25
How about running a simulation of what would happen: 
```
apt-get --dry-run remove fonts-dejavu-core fonts-dejavu-extra
```
On my system this produces a lot of output, showing it would remove several programs I use a lot and install some others instead. Not a situation I would want.
The packages xubuntu-core and xubuntu-desktop are the least problem of the stuff that would get removed, they are just meta-packages (empty packages with a lot of dependencies, used to install a lot of stuff in one go).

Holger

---

### Post by Furycd001 on 2019-02-25
> **Holger_Gehrke said:**
> How about running a simulation of what would happen: 
```
apt-get --dry-run remove fonts-dejavu-core fonts-dejavu-extra
```
On my system this produces a lot of output, showing it would remove several programs I use a lot and install some others instead. Not a situation I would want.
The packages xubuntu-core and xubuntu-desktop are the least problem of the stuff that would get removed, they are just meta-packages (empty packages with a lot of dependencies, used to install a lot of stuff in one go).

Holger

Thanks for the reply. Running apt gives me the same output as what I get when using synaptic. It wants to remove xubuntu-core & xubuntu-desktop. Since both are just meta-packages I assume I can remove them and not expect problems ??

---

### Post by Holger_Gehrke on 2019-02-25
The problem is whether the packages installed as dependencies of xubuntu-core and xubuntu-desktop are marked as automatically or manually installed. If they are marked as automatically installed the next 'apt autoremove' would get rid of them.You can use 'apt-mark showauto' and 'apt-mark showmanual' with a list of packages to get that status, but typing in that long list of packages is boring and the probability of errors is to high for my taste. I came up with
```
apt-mark showauto $(dpkg-query --show -f '${depends} ' xubuntu-desktop xubuntu-core|tr --delete ',')
```
to automate the process (replace 'showauto' with 'showmanual' to see which packages are not a problem ...). It showed two packages (libu2f-udev and spice-vdagent) which where marked as automatically installed. Running 'apt-mark manual libu2f-udev spice-vdagent' would mark them as manually installed and stop them from getting automatically removed. There might be other packages marked as automatic on your system.

Just out of curiosity: why do you want to remove that font ?

Holger

---

### Post by Furycd001 on 2019-02-25
Thank you for that very useful piece of code. Showauto gives me nothing in return & showmanual shows a list with xubuntu-core being on it, but I cannot see xubuntu-desktop anywhere on the list. I'm clearing out all unused fonts from my system because I design a lot of stuff in the likes of gimp & libre office and only want fonts that I actually have use for to be installed on my system. I sometimes scroll though my fonts when I'm trying to decide on one and it can get annoying seeing so many unused fonts that I never use or have no need for....

---

### Post by Holger_Gehrke on 2019-02-25
xubuntu-desktop not being on the list is quite right. It's a list of the dependencies of xubuntu-core and xubuntu-desktop. desktop depends on core but nothing in that list should depend on desktop, otherwise you'd have circular dependencies.

The list being empty for 'showauto' tells us that nothing would get marked for automatic removal if xubuntu-desktop and xubuntu-core were removed, which is as it should be.

Take a look at 'apt-cache rdepends fonts-dejavu fonts-dejavu-core fonts-dejavu-extra ttf-dejavu ttf-dejavu-extra ttf-dejavu-core'; that's a list of every package which either depends on this font or recommends or suggests it. Dejavu has been a standard font on various Linux distributions for a long time.

Holger

---

### Post by Furycd001 on 2019-02-25
This list of packages which depend / recommend this font is super long. Maybe I'll just leave it installed for now. Thank you very much for your help & insight....

---

