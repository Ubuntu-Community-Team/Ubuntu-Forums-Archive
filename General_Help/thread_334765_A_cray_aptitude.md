---
title: "A cray aptitude?"
date: 2007-01-09
forum: General Help
---

### Post by paparucino on 2007-01-09
Hi guys,

I'm running feisty ubuntu using some applications out of gnome like thunar and its plugins, mousepad and so on.
I was playing with aptitude and discovered it's crazy :-)
According to its opinion thunar, mousepad and other tools should be removed "because they are no longher used".
I'm using thunar instead of nautilus, mousepad instead of gedit on regular basis, so... how can aptitude state that they are no longer used?

Where is the problem?

---

### Post by Ramses de Norre on 2007-01-09
Did you explicitly install those packages or were they pulled in as dependency with some other package? If the latter: explicitly install them with aptitude.
If the first: try reinstalling them, if that wont work you should think about a bug maybe? Wouldn't be too surprising with an alpha state OS..

---

### Post by d3v1ant_0n3 on 2007-01-09
I believe it's recommended to use apt-get rather than aptitude in Feisty- aptitude can be a little heavy handed from what I've read.

---

### Post by paparucino on 2007-01-09
> **Ramses de Norre said:**
> Did you explicitly install those packages or were they pulled in as dependency with some other package? If the latter: explicitly install them with aptitude.
If the first: try reinstalling them, if that wont work you should think about a bug maybe? Wouldn't be too surprising with an alpha state OS..

I installed them via synaptic, but I think, if there is a bug, this isn't due to the new OS.

---

### Post by Ramses de Norre on 2007-01-09
> **d3v1ant_0n3 said:**
> I believe it's recommended to use apt-get rather than aptitude in Feisty- aptitude can be a little heavy handed from what I've read.

As far as I know it's just recommended to use aptitude instead of apt-get because aptitude is way better in dependency handling.

Things could have changed though ;)

---

### Post by paparucino on 2007-01-09
> **Ramses de Norre said:**
> As far as I know it's just recommended to use aptitude instead of apt-get because aptitude is way better in dependency handling.

Things could have changed though ;)
I agree with you. Someone told me that aptidude is reliabler than apt-get, but there is something strange with all these updater. Sometimes I suspect that aptidute, synaptic and apt-get hate each other. :-) 
Well... I always use synaptic without any problem, to do a distro update, sometime I use apt-get to install new packages and I use aptitude when I want "to play". 
Sometimes when I run aptitude I get strange results. E.g. before writing the initial post according to aptitude I had 49 broken files, none according apt-get and synaptic.
BOH?!???!?!

---

