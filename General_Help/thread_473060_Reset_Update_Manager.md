---
title: "Reset Update Manager???????"
date: 2007-06-13
forum: General Help
---

### Post by calou on 2007-06-13
First of all you should know I'm a newbee to Linux and Ubuntu.   A couple of days ago I was trying to download and install Virtualbox, it appeared to me that install  was hung so I canceled it and tied to restart it and made a bunch of newbee mistakes . . .  too many to even begin to discuss but the end result is that Update Manager now seems to be in a non-functional state.   When I try to run it I get the message:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

I can't get it to reinstall (and at this point I don't care to reinstall it, all I want to do is get Update Manger to work).

When I do  sudo dpkg -i virtualbox from the terminal I get the following:

dpkg: error processing virtualbox (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox

When I do  sudo dpkg -C I get the following:

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 virtualbox  

When I do  sudo dpkg -s virtualbox I get the following:

Package: virtualbox
Status: deinstall reinstreq half-installed
Priority: optional
Section: misc
Version: 1.4.0-21864_Ubuntu_feisty


When I do sudo dpkg -r virtualbox I get the following:

dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox

I've tried using the force option and everything else on the dpkg --help menu that looks as if it could work including -force -remove-reinstreq <package name> to no avail; right now all I'm interested in is getting Update Manager to forget about the failed install and allow it to run so I can use it to update Ubuntu and my softwares.   Is there anyone who knows a way to "reset" update manager and get it to forget the failed install of Virtualbox.  If I could get rid of the  "half-installed" Virtualbox it would be a plus but right now I'm just interested in is getting Update Manager to work the way it did before I screwed things up, surely I'm not the first person who's ever done this . . . . am I?????  Help :D

---

### Post by zvacet on 2007-06-13
```
sudo aptitude --purge remove virtualbox
```

or you can do it manualy

```
whereis virtualbox
```

You wil get a list of directories with virtualbox files.Go to the every of them by typing (for example)

```
cd /usr/bin
```
when you are inside type** ls** and you will see virtualbox file.still in same directory remove it 

```
sudo rm -r file_name
``` 

file_name =exact name of virtualbox file in that directory

When you done it your update-manager will work again.

---

