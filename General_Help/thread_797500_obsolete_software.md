---
title: "obsolete software"
date: 2008-05-17
forum: General Help
---

### Post by vvule on 2008-05-17
I`ve made a little mistake during upgrade to 8.04. I`ve left the obsolete software on disk (if it is a mistake).Anyway I would like to erase it, but I do not intend to check package by package. 
Does anyone know how to do it in an easy way. If such way exists?

---

### Post by macaholic on 2008-05-17
What do you mean by obsolete software exactly? Please clarify.

---

### Post by ibuclaw on 2008-05-17
Obselete = Software Installed on the system that is not in the Repository / Is no longer maintained by the Repository.

Regards
Iain

---

### Post by macaholic on 2008-05-17
> **tinivole said:**
> Obselete = Software Installed on the system that is not in the Repository / Is no longer maintained by the Repository.

Regards
Iain
I know what the definition of obsolete software is, I jsut wanted to make sure what he was referring to as obsolete software was the same thing that i know it is.

---

### Post by vvule on 2008-05-17
It was nice to read this academic conversation,:)but does anyone know how to erase it?

I`ve press mistakenly "keep it" insted of "delete it", at the very end of upgrade!

---

### Post by Mr A Mouse on 2008-05-17
The only way I know of is to go through it package by package. However, is this a huge amount of packages, or is this just a few odds and ends. If the latter, I would probably leave them alone unless they caused problems, or perhaps just erase a package when I came across it in normal operation.

---

### Post by ibuclaw on 2008-05-17
What software packages do you have installed that are marked as obsolete?

As you may not want all of them gone...

For example, I have:
avast4workstation
codeblocks
gaim-xfire
love
tuxguitar
ubuntutweak
virtualbox

All of which I **don't** want to be removed.

Whereas packages like "**liblaunchpad-integration0**" have already been superceded by other packages, and so you will not be affected by their removal.

Open up "**synaptic**" and choose to view the packages by "**Status**". Then select "**Installed (local or obsolete)**".

[EDIT]
Look at the screenshot:
[[IMG]http://img177.imageshack.us/img177/2292/screenshotsynapticpackazw9.th.png[/IMG]](http://img177.imageshack.us/my.php?image=screenshotsynapticpackazw9.png)

Regards
Iain

---

### Post by vvule on 2008-05-17
The question is how can I find out if the package is superceded
 or not?

For example, there are some packages for previous kernel versions

And also when I start the Update Manager there are two packages which are on the list for update
Recommended updates - libtotem plparser10
Distribution upgrades - libgtk 1.2

but I can`t check them

---

### Post by ibuclaw on 2008-05-17
Open a terminal and type in:
```
dpkg -l | grep packagename | sed 's/         / /g'
```

Replace "packagename" with the keyword of that packagename.

ie: liblaunchpad
```

dpkg -l | grep liblaunchpad | sed 's/         / /g'
ii  liblaunchpad-integration0         0.1.16     library for launchpad integration
ii  liblaunchpad-integration1         0.1.19     library for launchpad integration

```

As we see. We have two packages. and the package "integration1" has a version number higher than "integration0".

So we can assume that "integration0" has been superceded by the new, non-obsolete package, and it is safe to remove.

Regards
Iain

---

### Post by vvule on 2008-05-17
Thanks tinivole, that prety much helped, but I came acroos an awkard situation

When I typed this

dpkg -l | grep libbrlepi | sed 's/         / /g'

The systems threw a two versions ob libbrlepi - 
libbrlepi0.5
libbrlepi1,

but libbrlepi1 was on an obsolete list, and had lower ubuntu..... number after the designation of the package.

I chosed to erase libbrlep1, but it also took away one dependecy with it, one which name begins with python-...

Did I make the right choice?

---

### Post by ibuclaw on 2008-05-17
> **vvule said:**
> Thanks tinivole, that prety much helped, but I came acroos an awkard situation

When I typed this

dpkg -l | grep libbrlepi | sed 's/         / /g'

The systems threw a two versions ob libbrlepi - 
libbrlepi0.5
libbrlepi1,

but libbrlepi1 was on an obsolete list, and had lower ubuntu..... number after the designation of the package.

I chosed to erase libbrlep1, but it also took away one dependecy with it, one which name begins with python-...

Did I make the right choice?

If the following packages have the same version number, then yes:
[LIST]
[*]brltty - 3.9-6ubuntu1
[*]python-brlapi - 3.9-6ubuntu1
[*]libbrlapi0.5 - 3.9-6ubuntu1
[/LIST]
Regards
Iain

---

