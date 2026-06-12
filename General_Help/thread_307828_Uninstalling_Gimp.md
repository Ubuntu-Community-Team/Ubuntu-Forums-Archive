---
title: "Uninstalling Gimp"
date: 2006-11-27
forum: General Help
---

### Post by Gorlist on 2006-11-27
Hi, quick question in regards to uninstalling Gimp - Ive marked it for removal through the Synaptic Package Manager, when I go to press apply and check to see what packages its really wanting to remove it also lists the **Ubuntu-Desktop**!!

To me this sounds rather dangerous and inadvisable, or is it just a grammatical error??

Also whilst im posting, one thing ive have noticed with Ubuntu, if you copy some text from say Evolution mail and then close the compose email window, you can't then paste the information you copied onto another form (e.g. Ubuntu Forum messages!) - this is fine aslong as you remeber :) Is thier any reason for this as it effects all applications? 

Regards!

---

### Post by Jussi Kukkonen on 2006-11-27
Ubuntu-desktop is just a meta-package: Having it installed ensures that you have all the programs that a default Ubuntu install has. Removing it does not remove any functionality.

However, if you ever do a OS upgrade, you should re-install ubuntu-desktop before upgrading. That way you get all the new software that may be included in the new Ubuntu version.

---

### Post by engla on 2006-11-27
Well nothing is wrong. What this means is that Gimp is part of the packages that are installed by default. Removing ubuntu-desktop doesn't remove anything, it's really just a marker package that tells you that you have _all_ the packages that come with ubuntu by default.

So, it's no problem to remove gimp and ubuntu-desktop. However, there can be other problems further down the road, if you remove a lot of packages, but only really when upgrading to a new release. It is recommended to reinstall the package ubuntu-desktop (and thus gimp and other things that it depends on) before dist-upgrading.

---

### Post by CatKiller on 2006-11-27
ubuntu-desktop is a meta-package that depends on all the component parts of the Ubuntu desktop distribution. If you remove one of the component parts, then you necessarily don't have the Ubuntu desktop distribution.

Removing it isn't a problem, but it's generally advised to reinstall it before you do a dist-upgrade to avoid potential problems.

EDIT: I'm slow today.

---

### Post by Gorlist on 2006-11-27
Thanks for mightily quick replies!! Ok, I will leave it then - Gimps good, but very annoying as for some reason it decided to become primary application to open image files (just worked out how to define Open With program defaults :) )

Perhaps as a suggestion the Ubuntu-Desktop meta package should be renamed or include a marker just to explain, its slightly worrying for someone who doesn't know :)

Thanks again!

---

