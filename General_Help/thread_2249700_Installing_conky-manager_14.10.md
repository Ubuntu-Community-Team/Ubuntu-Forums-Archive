---
title: "Installing conky-manager 14.10"
date: 2014-10-24
forum: General Help
---

### Post by UnMeilleurReve on 2014-10-24
[COLOR=#333333][FONT=monospace]I am trying to install conky-manager via " sudo apt-get install conky-manager " and receiver the following terminal error:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]
The following packages have unmet dependencies:
 conky-manager : Depends: conky-all but it is not installable
E: Unable to correct problems, you have held broken packages.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]
When I do the sensible thing and try sudo apt-get install conky-all I receive:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package conky-all is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  conky-std:i386 conky-cli:i386 conky-std conky-cli[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]E: Package 'conky-all' has no installation candidate

Can anybody help me either convince conky-manager to use just plain old conky, how to find and install conky-all, or how to rename plain old conky to conky-all in such a way that conky-manager will understand that I meet the dependencies? In such a way that a newbie with a fresh install of 14.10 can do it from terminal?[/FONT][/COLOR]

---

### Post by iceman1411 on 2014-10-24
First, run sudo apt-get -f install to make sure any broken dependencies
 are met. If you are still having issues with conky-all, you may want to purge it from your system and reinstall:
```
sudo apt-get purge conky-all
sudo apt-get install conky-all
```

Also, have you already added the ppa for conky-manager? It is not included in the repositories so if you have not done so:

```
sudo add-apt-repository ppa:teejee2008/ppa
```
then run:
```
sudo apt-get update
sudo apt-get install conky-manager
```

Hope this helps.

---

### Post by CatKiller on 2014-10-24
conky-all isn't in the [utopic repositories]("http://packages.ubuntu.com/search?keywords=conky-all").

---

