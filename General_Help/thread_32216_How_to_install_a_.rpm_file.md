---
title: "How to install a .rpm file?"
date: 2005-05-06
forum: General Help
---

### Post by eQuin on 2005-05-06
My question is, how i can install a .rpm file because i have a programm with this ending, so what can i do now?

---

### Post by enquiry on 2005-05-06
Use Alien:
alien -d /path/to/.rpm 
creates a deb package from the rpm package.

---

### Post by eQuin on 2005-05-06
hmm, i write the correct path and it starts but then it abort and say, that a file could not be found!
is there a other way to user .rpm?

---

### Post by az on 2005-05-06
cd to the directory with the rpm

sudo alien -i <file.rpm>

---

### Post by thoms on 2005-05-06
[QUOTE=eQuin]My question is, how i can install a .rpm file because i have a programm with this ending, so what can i do now?[/QUOTE]
 I think it'd be worth pointing out what's going on here. Basically you should try and download .deb (debian) files because they'll generally install better (as Ubuntu's based on Debian).

What the alien command is essentially doing is converting the file to a Ubuntu friendly format.

---

### Post by eQuin on 2005-05-07
ok, it's now a .deb file!
how can i install now the .deb file?

---

### Post by WakkiTabakki on 2005-05-07
[QUOTE=eQuin]ok, it's now a .deb file!

how can i install now the .deb file?[/QUOTE]

```
$> sudo dpkg -i yourfile.deb
```

Once you've done this, it should be installed and also turn up in synaptics, so you can uninstall it from there!

Good luck
N

---

### Post by bored2k on 2005-05-07
[QUOTE=WakkiTabakki]```
$> sudo dpkg -i yourfile.deb
```

Once you've done this, it should be installed and also turn up in synaptics, so you can uninstall it from there!

Good luck
N[/QUOTE]
 I would suggest
```
sudo dpkg -i file.deb && apt-get -f install
```To get rid of dependency problems/.

---

