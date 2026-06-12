---
title: "run OpenOffice 2.2 NOT from sudo"
date: 2007-01-21
forum: General Help
---

### Post by munkar on 2007-01-21
i managed to install OpenOffice.org 2.2 (the developers' snapshot), using [this tutorial]("http://download.openoffice.org/2.1.0/instructions.html"). what i don't understand is how to make it run without having to go to sudo all the time -- which makes all of the docs i save owned by ROOT.

it has something to do with putting something in /usr/bin?....

---

### Post by mexlinux on 2007-01-23
I must not run openoffice as root,
why do you say you need to?
the binary should be somewhere in /opt/openoffice or simmilar, just run that app.

---

### Post by munkar on 2007-01-25
no, the point is i want it NOT to run as root, which is what it's doing right now. how do i make it run "locally," if that's the right term?

---

### Post by taurus on 2007-01-25
Do you know where the latest version of OpenOffice installed to on your machine?  Run it from there.

---

### Post by eldepeche on 2007-01-25
Those instructions are for Windows...

---

### Post by paulg on 2007-01-25
Locate where the application is installed (as suggested earlier, /opt/OpenOffice is a good start).

Check what the ownership/permisions of the the directory and files are. I suspect the ownership is root:root ([user]:[group]). If you change the ownership to root:user anyone on the system should be able to run it.

I believe the command would be

```

sudo chown -R root:user [path to the directory]

```

chown is the command that allows you to change the ownership of a file/directory.
-R is the option to make the chown command recursive.
'root' is the owner of the file/directory.
'user' is the file/directory group. 
You need to include the path to the directory.

Assuming the group permissions are set appropriately, anyone that is part of the 'user' group should be able to run the program afterward.

---

### Post by munkar on 2007-01-26
> Those instructions are for Windows...

sorry, wrong URL....[here are the hints i followed]("http://installation.openoffice.org/servlets/ReadMsg?list=dev&msgNo=609").

> sudo chown -R root:user [path to the directory]

thanks. i did this, and am now able to run it locally, but now it freezes on me as soon as i try to open up any document. wonderful.

---

### Post by paulg on 2007-01-26
Sorry it didn't work for you. If you are running it in the shell post any errors you are getting and someone else might be able to help you out. Perhaps it is as simple as a missing dependency?

Good luck,

~pAul.

---

### Post by munkar on 2007-01-26
thanks, paul, actually it just started working, without my having changed anything. the only thing now is that i have to force it to quit -- it won't exit or even close a document otherwise.

---

