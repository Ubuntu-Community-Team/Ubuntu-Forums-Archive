---
title: "Cuda package error"
date: 2019-03-05
forum: General Help
---

### Post by clement-2000 on 2019-03-05
Hi experts, 
I tried to install the drivers for my Nvidia Cuadro K2200 following a tutorial, and it just failed. 

```
clement@clement-fixe:~$ sudo apt-get install nvidia-cuda-toolkit g++-5 nvidia-modprobe
```

So now I have some package errors, and I don't know how to fix it. 

I'd just like to remove everything first. 
So here is the error I'm getting (sorry, it's in french, **if you need translation, please ask**). 

```
clement@clement-fixe:~$ sudo apt-get install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 cuda-libraries-dev-10-1 : Dépend: libcublas-dev (>= 10.1.0.105) mais il n'est pas installé
 cuda-samples-10-1 : Dépend: libcublas-dev (>= 10.1.0.105) mais il n'est pas installé
 cuda-visual-tools-10-1 : Dépend: libcublas-dev (>= 10.1.0.105) mais il n'est pas installé
E: Dépendances non satisfaites. Essayez « apt --fix-broken install » sans paquet
   (ou indiquez une solution).
```

Thanks in advance for your help, 
Clément.

---

### Post by monkeybrain20122 on 2019-03-05
Cuda 10.1 has moved the  libcublas files and it seems to break the installation. There are a few people reporting problems.[URL="https://devtalk.nvidia.com/default/topic/1048021/cuda-setup-and-installation/error-depends-libcublas-dev-gt-10-1-0-105-but-it-is-not-installed-ubuntu-18-04/"]

https://devtalk.nvidia.com/default/topic/1048021/cuda-setup-and-installation/error-depends-libcublas-dev-gt-10-1-0-105-but-it-is-not-installed-ubuntu-18-04/[/URL]  [URL="https://devtalk.nvidia.com/default/topic/1047973/cuda-setup-and-installation/system-update-wants-to-remove-cuda-10-and-related-seemingly-w-no-replacement/"]
https://devtalk.nvidia.com/default/topic/1047973/cuda-setup-and-installation/system-update-wants-to-remove-cuda-10-and-related-seemingly-w-no-replacement/[/URL]

I would just stay on cuda10.0 and wait for Nvidia to fix the bugs. Since you are using the cuda repo this is very easy.
```
sudo apt remove cuda
sudo apt autoremove
sudo apt update
sudo apt install cuda-10-0
```

First line remove the cuda meta-package (so apt won't try to upgrade to cuda-10.1 later)
Second line actually remove all the cuda-10.1 packages
third line update the database
forth line install the cuda-10.0 meta-package and all the cuda-10.0 packages.

Don't do anything with the nvidia driver, you don't need to touch that to switch cuda. In some forum posts they told people to purge everything nvidia and revert to nouveau that is nonsense.

---

### Post by clement-2000 on 2019-03-07
THANK YOU !!
Everything is back and working !
I can even use my overpowered GPU in blender !

---

