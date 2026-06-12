---
title: "Repositories....help needed"
date: 2005-10-15
forum: General Help
---

### Post by nicomazi on 2005-10-15
hi all,
tryed to add some aplications (though "add aplication" menue) and i get this;
               > This program is not currently installable. It should be available in the "universe" section of the repository. Enable that section in the Repositories dialog in the Settings menu to install it.

knowing that adding/activating repositories can be tricky (well...for me anyways) lpease tell me how to do this. 
thnx

---

### Post by DJ_Max on 2005-10-15
Uncomment the lines in your /etc/apt/sources.list that mentions 'universe'.

Then
```
sudo apt-get update
```

Even better, [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Arktis on 2005-10-15
Edit: nevermind.

---

### Post by lithorus on 2005-10-15
Actually when I tried to add stuff through the Add Applications it just asked me if I wanted to add the universe repositories. No need to edit config files :)

---

### Post by nicomazi on 2005-10-15
[QUOTE=lithorus]Actually when I tried to add stuff through the Add Applications it just asked me if I wanted to add the universe repositories. No need to edit config files :)[/QUOTE]

i tryed to do the same and Add Aplicatin asked me too if i wanted to add this repository but then i got this:   
                 > W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

any ideas what does it means?

PS actually repositories were added...i could download things, but why i got this error message - i don't know

---

