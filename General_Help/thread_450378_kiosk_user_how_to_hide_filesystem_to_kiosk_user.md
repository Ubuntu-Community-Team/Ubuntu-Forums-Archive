---
title: "kiosk user: how to hide filesystem to kiosk user"
date: 2007-05-21
forum: General Help
---

### Post by suoko on 2007-05-21
Hi,

I'm setting up some kiosk workstations which only have to let users surf the internet.
I would like the user to only see his home directory, which means opening nautilus he should be able to see  only his /home/kiosk directory.
Anything below (or above?) that directory (ie /etc, /var, /usr, etc...), should be inaccessible AND unbrowsable.
At them moment he can browse those folders.

How can I do it?
I'd like to do that through groups using users-admin, if possible.

thanks
G.

---

### Post by aysiu on 2007-05-21
The kiosk program you're using should let you do that. What kiosk program are you using?

---

### Post by suoko on 2007-05-22
I use pessulus ...
but there's no option for what I wanted to do...

---

### Post by suoko on 2007-05-29
ok, a command line solution to my problem is welcome :-)
I have no problems with command line. I'm just willing to see everything with a powerful gui...
any hints?

---

### Post by ezrollers on 2007-05-29
I suppose you could recursively remove the read permission to everything on the filesystem (/)

chmod -R 000 / or smth like that

then

chmod -R 444 /home/user 

to grant read rights to the home directory

that way your user should be able to see / but not browse it and have read access to his home folder

is this what you were looking for?

---

### Post by suoko on 2007-06-04
Actually I'd like to leave / permissions untouched.
I'd like just to set the upper folder of Nautilus to /home/kioskuser
A gconf option would be nice...

---

### Post by Jose Catre-Vandis on 2007-06-06
Its not the complete solution (I'll explain later) but you can place a file called
```
.hidden
``` in your root filesystem (browse Filesystem in nautilus

You then open up .hidden and list all the directories you want to hide and save

You will then see that only the root folder "Filesystem" is viewable and nothing below it

The crack in the paintwork is that a simple CTRL + H, or a trip to View > Show Hidden Files, undoes this good work.

All that is need is to remove the show hidden files option (this would be a good thing with regards to what lies in /home in any case for kiosk use.

maybe there is a setting in gconf-editor that I can't find that disables the ability to see hidden files?

---

### Post by Jose Catre-Vandis on 2007-06-25
> **Jose Catre-Vandis said:**
> All that is need is to remove the show hidden files option (this would be a good thing with regards to what lies in /home in any case for kiosk use.

maybe there is a setting in gconf-editor that I can't find that disables the ability to see hidden files?

Anyone?

---

