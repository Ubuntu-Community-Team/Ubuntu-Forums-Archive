---
title: "Google Repositories"
date: 2008-07-03
forum: General Help
---

### Post by TheSeb on 2008-07-03
I added Google Repositories according to this tutorial
[http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html)

However when I go to Add/Remove programs I still do not see Picasa (the program I want to add)
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

Why is that? The only thing I can think of is that the tutorial is for Feisty and I'm using Hardy. Does that matter? What am I doing wrong? :(

---

### Post by milosz.galazka on 2008-07-03
(For fast check) I just added a line
```
deb http://dl.google.com/linux/deb/ stable non-free
```
to file */etc/apt/sources.list*
then run
```
sudo apt-get update
```
then 
```
sudo apt-get install picasa
```
and it's downloading package...

---

### Post by TheSeb on 2008-07-04
> **milosz.galazka said:**
> (For fast check) I just added a line
```
deb http://dl.google.com/linux/deb/ stable non-free
```
to file */etc/apt/sources.list*
then run
```
sudo apt-get update
```
then 
```
sudo apt-get install picasa
```
and it's downloading package...


Thanks it worked, yet I still do not understand why the programs that I add such as Picasa and Exaile do not show up in the add/remove panels at all. I thought that after you add Repositories they become part of the add/remove segment. I am so confused about linux :(

---

### Post by ryanhaigh on 2008-07-04
You probably need to change the option from all supported software to all available software (top right). Not sure if thats the wording exactly but it basically means show packages from universe/multiverse. You might find synaptic (system>admin>synaptic) more to your liking.

---

### Post by TheSeb on 2008-07-04
> **ryanhaigh said:**
> You probably need to change the option from all supported software to all available software (top right). Not sure if thats the wording exactly but it basically means show packages from universe/multiverse. You might find synaptic (system>admin>synaptic) more to your liking.

No, no matter what I do... even when i switch to all available soft. I still do not see Picasa (From Google Repos.) etc. Would someone know why?

---

### Post by milosz.galazka on 2008-07-04
I just checked using *synaptic* and I see Picasa package...

Try using *aptitude* to look for it... it will be there,
this is strange problem.

---

