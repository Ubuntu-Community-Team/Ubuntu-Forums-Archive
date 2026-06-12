---
title: "win32 codecs"
date: 2004-11-22
forum: General Help
---

### Post by anklator on 2004-11-22
hi,

i am having some problems to install win32 codecs on ubuntu, the thing is that i can play videos in kaffeine(kde multimedia player), but it doesnt work totem, btw i have universe and multiverse enabled and i cant get the codecs by apt, any clue?

:edit: root@ubuntu-xabier:/home/xabier # apt-get install w32codecs
Pakete Zerrenda irakurtzen... Eginda
Dependentzia zuhaitza eraikitzen... Eginda
w32codecs paketea ez da eskuragarria, baina beste pakete batenbatek
 honi erreferentzia egiten du. Honek paketea falta dela, zaharkiturik
 dagoela edo beste jatorri batetatik bakarrik eskuratu daitekeela
esan nahi du
E: w32codecs paketea ez da instalagarria
root@ubuntu-xabier:/home/xabier #

this means that i cant get the package, but there is a refernce in other package, E: w32codecs package is not instalable

---

### Post by amoser on 2004-11-22
add this line to your sources.list (/etc/apt/) - deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main.

Open synaptic, search for totem, and install totem-xine.  It will remove some packages, don't worry about it.

Then search for w32, and install w32codecs.

There you go, complete multimedia for gnome.

~Alan

---

### Post by anklator on 2004-11-22
its already working, can i play dvds, or do i need something more??

thanks

---

### Post by calvinpriest on 2004-11-22
If it isn't installed already, you'll need to do:
sudo apt-get install libdvdcss2

This is also from the marillat repository mentioned above.

---

### Post by amoser on 2004-11-22
You don't need the libdvdcss2 package to play dvd with totem-xine, it has it built in.

~Alan

---

### Post by jdong on 2004-11-22
well, it never hurts... :roll:

---

