---
title: "Problem in fonts"
date: 2007-11-16
forum: General Help
---

### Post by scoo007 on 2007-11-16
Hi,
can any one help me in installation Hebrew fonts and Microsoft fonts 

please

---

### Post by mojoman on 2007-11-17
The package for microsofts fonts are called msttcorefonts and to install it you have to enable the unfree repository (at least I think it's in the unfree but it's in one of the standard Ubuntu repositories anyway). This is controlled by the file /etc/apt/sources.list but if you're uncomfortable with editing system files an easy way to enable them is to do it add/remove program application or in synaptic (I forgot which one as I never use them).

to install msfonts through terminal, just type
```

sudo apt-get update && sudo apt-get install msttcorefonts
```

Note that you have to enable the extra repositories before doing this.

You could also use synaptics and do a search for msttcorefonts, find it in the list, clicck the little box and press apply.

As for hebrew fonts, do a search in synaptics, or if you prefer the command line you can try something like this:

```
apt-cache search hebrew
```

and if that list is too long do 

```
apt-cache search hebrew | grep font
```

That should produce a list of all fonts that have the word hebrew in the description.

---

