---
title: "tetex-extra package"
date: 2005-09-04
forum: General Help
---

### Post by inechita on 2005-09-04
Ive just installed the tetex-extra package from a Debian repository (experimental) and it has broken dependencies with my other tetex packages (which come from ubuntu repositories). when i try to uninstall the package with 
```

sudo dpkg -r --force-all tetex-extra
```

I get 
```
(Lecture de la base de données... 73477 fichiers et répertoires déjà installés.)Suppression de tetex-extra ...
Running updmap-sys. This may take some time. ...
updmap failed. Output has been stored in
/tmp/tetex.updmap.XXrUgfwS
Please include this file if you report a bug.
dpkg : erreur de traitement de tetex-extra (--remove) :
 le sous-processus post-removal script a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution :
 tetex-extra
```

How can I get past this issue and install the ubuntu tetex-extra package in place ?

thanks a lot, 

Ion

---

### Post by parktownprawn on 2005-09-04
what happens if you just try
```
sudo dpkg -r  tetex-extra
```

---

### Post by inechita on 2005-09-04
[QUOTE=parktownprawn]what happens if you just try
```
sudo dpkg -r  tetex-extra
```[/QUOTE]

```
thant@home:~$ sudo dpkg -r  tetex-extra
(Lecture de la base de données... 73477 fichiers et répertoires déjà installés.)Suppression de tetex-extra ...
Running updmap-sys. This may take some time. ...
updmap failed. Output has been stored in
/tmp/tetex.updmap.XXiGtzW3
Please include this file if you report a bug.
dpkg : erreur de traitement de tetex-extra (--remove) :
 le sous-processus post-removal script a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution :
 tetex-extra
thant@home:~$ sudo cat /tmp/tetex.updmap.XXiGtzW3
/var/lib/dpkg/info/tetex-extra.postrm: line 161: updmap-sys: command not found

```

---

### Post by parktownprawn on 2005-09-04
Sorry I have no idea.

Do you know what updmap-sys is?

---

### Post by inechita on 2005-09-04
No, I don't. 

Thanks anyway,

Ion

---

### Post by parktownprawn on 2005-09-04
You could try contact the maintainers of the package:

[email]debian-tetex-maint@lists.debian.org[/email]

since ["Users of experimental packages are encouraged to contact the package maintainers directly in case of problems."](http://packages.debian.org/experimental/tex/tetex-extra)

---

### Post by inechita on 2005-09-04
[QUOTE=parktownprawn]You could try contact the maintainers of the package:

[email]debian-tetex-maint@lists.debian.org[/email]

since ["Users of experimental packages are encouraged to contact the package maintainers directly in case of problems."](http://packages.debian.org/experimental/tex/tetex-extra)[/QUOTE]

this has probably nothing to do with the package. It's most likely due to my stupidity in installing the Debian package and not the Ubuntu one.

---

### Post by parktownprawn on 2005-09-04
i guess 
/var/lib/dpkg/info/tetex-extra.postrm 
is a shell script that gets run as part of the process of removing the package.

its giving an error because you don't have 
updmap-sys installed.

I have updmap on my ubuntu machine - it updates  
font map files for TeX output drivers.


the ubuntu version of   
/var/lib/dpkg/info/tetex-extra.postrm 
on my machine is only 42 lines long so the debian experimental version is doing a whole lot more.

short of  messing with the script
/var/lib/dpkg/info/tetex-extra.postrm
i'm not sure what you should do ( you could try comment out line 161 which is giving the error but that may do more harm than good). 

I advise taking advice from someone more knowledgable than me.

---

