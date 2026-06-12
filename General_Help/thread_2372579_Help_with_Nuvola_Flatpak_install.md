---
title: "Help with Nuvola Flatpak install"
date: 2017-09-26
forum: General Help
---

### Post by CaptainMark on 2017-09-26
I've been trying to update Nuvola player on Ubuntu 16.04, it seems the team have moved to Flatpak which I know nothing about yet. I've been following the instructions here [https://nuvola.tiliado.eu/nuvola/ubuntu/xenial/](https://nuvola.tiliado.eu/nuvola/ubuntu/xenial/) but I get a permission denied error as can be seen here
```

[18:58:11] mark@desktop ~ $ flatpak install --from https://nuvola.tiliado.eu/eu.tiliado.Nuvola.flatpakref
This application depends on runtimes from:
  https://sdk.gnome.org/repo/
Configure this as new remote 'gnome' [y/n]: y
Installing: eu.tiliado.Nuvola/x86_64/stable
Required runtime for eu.tiliado.Nuvola/x86_64/stable (org.gnome.Platform/x86_64/3.24) is not installed, searching...
Found in remote gnome, do you want to install it? [y/n]: y
Installing: org.gnome.Platform/x86_64/3.24 from gnome
error: Permission denied

```
I'm no expert but this seems rather than an error in their package is probably an error in the Flatpak command they ask you to use.

Any one know how to sort this error out, I don't want to just add sudo in case that isn't the right thing to do with Flatpaks

Regards
Mark

---

### Post by CaptainMark on 2017-09-29
Shameless bump!

---

