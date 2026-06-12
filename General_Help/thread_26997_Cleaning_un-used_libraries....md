---
title: "Cleaning un-used libraries..."
date: 2005-04-14
forum: General Help
---

### Post by Spudgun on 2005-04-14
Hi there,
Can anyone tell me how I could clean/get rid of all un-used libraries on my system? I feel like a spring clean and I don't like having anything cluttering my hard drive. 

Thanks in advance,
Spudgun

---

### Post by dcast on 2005-04-14
Go into synaptic and click on the libraries on the right. Then select mark for complete removal and then click apply on the top toolbar.

---

### Post by Spudgun on 2005-04-14
Ok thanks alot, but is there a way to determine which libraries aren't being used anymore?

---

### Post by speedman on 2005-04-14
deborphan is your friend.  Just run the command deborphan in a term and then do a sudo apt-get remove --purge <pkg_names>.

You should run deborphan several times as it usually turns up additional orphaned packages after you remove the first batch.


Regards,

SM

---

### Post by Spudgun on 2005-04-14
Cheers :D

---

### Post by stevetone on 2005-04-14
[QUOTE=speedman]deborphan is your friend.  Just run the command deborphan in a term and then do a sudo apt-get remove --purge <pkg_names>.

You should run deborphan several times as it usually turns up additional orphaned packages after you remove the first batch.


Regards,

SM[/QUOTE]

Or you could, like I did, combine them into one command:

sudo apt-get remove --purge `deborphan`

Beats typing in a list of cryptic names!

---

### Post by speedman on 2005-04-14
[QUOTE=stevetone]Or you could, like I did, combine them into one command:

sudo apt-get remove --purge `deborphan`[/QUOTE]

I would not recommend doing that.  deborphan isn't flawless and neither are all package deps.  Sometimes deborphan will suggest the removal of packages that should definitely not be removed and due diligence should be shown before accepting all of it's suggestions.

> Beats typing in a list of cryptic names!

No need to type anything.  Double click on the package name to highlight it and wheel click to paste it back on the command line.  Or, if that's still too much work, but you still want to go over the list of packages before proceeding you can do this:

deborphan > pkgs

vi pkgs

... and remove any entries that you are unsure of, or that you know should stay on your system.  Then ...

sudo apt-get remove --purge $(cat ./pkgs)

Btw, using back ticks to enclose shell statements has been deprecated since bash 2.x and $(shell_arg) should be used instead.


Regards,

SM

---

