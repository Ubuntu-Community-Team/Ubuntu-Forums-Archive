---
title: "aptitude vs. apt-get"
date: 2007-06-26
forum: General Help
---

### Post by stchman on 2007-06-26
I see that most folks here use apt-get.  I have read that aptitude is the way to go.

What are the advantages and dis-advantages of both.

Thanks

---

### Post by mikewhatever on 2007-06-26
Frankly, I can't see why both apt-get and aptitude are needed 
[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

---

### Post by rillip on 2007-06-26
I perfer apt-get.  I don't want the software to start removing things for me.  Adding things, no problem, removing, uh uh.

There are anecdotal cases where aptitude will remove "too much" when uninstalling a program, i.e. removing thinks it things aren't  used, but in fact are.  This probably occurs when you've installed something through another means, and aptitude doesn't know the program is installed and using it.

If you're going to use apttitude, I recommend ALWAYS using aptittude for just such a reason.  Mixing and matching is ugly because it maintains its own list of what has been installed and uses that, while apt-get relies on dpkg to determine that.

---

### Post by EndPerform on 2007-06-26
It's always been my experience that aptitude will remove whatever it installed with a particular package, and haven't ever had it try to remove something else that was needed.  Once I used aptitude, there was no going back.  Additionally, aptitude has a curses interface which you can browse packages, etc.

---

### Post by Sweet Mercury on 2007-06-26
> **stchman said:**
> I see that most folks here use apt-get.  I have read that aptitude is the way to go.

What are the advantages and dis-advantages of both.

Thanks

Apparently apt-get used to be pretty bad with dependencies, but according to the psychocats tutorial, that's no longer the case.

Aptitude has that pseudo-GUI, but I don't like that much; it's awkward at best. I use synaptic to browse packages.

---

### Post by az on 2007-06-26
> **EndPerform said:**
> Additionally, aptitude has a curses interface which you can browse packages, etc.

Want a hard-core curses interface to your packages?

sudo dselect

---

### Post by az on 2007-06-26
> **Sweet Mercury said:**
> Apparently apt-get used to be pretty bad with dependencies

To clarify, all packages are installed using dpkg and a dependency is a dependency.  You will not break your system by using one package manager fronted (apt-get or aptitude) over the other because all the package tools call dpkg to install the packages onto your system.  Dpkg is also used to remove each package.  Dpkg is the core of the package manager.

What aptitude tries to do is remember what you installed and remove extra packages.  On the other hand, you will never break your system by leaving some packages behind.  By and large, packages do not even take up all that much disk space.

---

### Post by Sweet Mercury on 2007-06-26
> **az said:**
> To clarify, all packages are installed using dpkg and a dependency is a dependency.  You will not break your system by using one package manager fronted (apt-get or aptitude) over the other because all the package tools call dpkg to install the packages onto your system.  Dpkg is also used to remove each package.  Dpkg is the core of the package manager.

What aptitude tries to do is remember what you installed and remove extra packages.  On the other hand, you will never break your system by leaving some packages behind.  By and large, packages do not even take up all that much disk space.

Ah. I'm still new to the whole dependency thing and exactly how that works. I haven't had any issues like that though.

I assume that Synaptic uses dpkg as well?

---

### Post by az on 2007-06-26
> **Sweet Mercury said:**
> Ah. I'm still new to the whole dependency thing and exactly how that works. I haven't had any issues like that though.

I assume that Synaptic uses dpkg as well?

Synpatic is a frontend to apt.  So is Add-Remove Programs.  Apt is a frontend to dpkg.

---

### Post by Sweet Mercury on 2007-06-26
> **az said:**
> Synpatic is a frontend to apt.  So is Add-Remove Programs.  Apt is a frontend to dpkg.

Well there it is. Thanks.

---

### Post by EndPerform on 2007-06-28
> **az said:**
> Want a hard-core curses interface to your packages?

sudo dselect

Ah yes, almost forgot about that, too.  Definitely hardcore.

---

### Post by nick_h on 2007-06-29
> **az said:**
> What aptitude tries to do is remember what you installed and remove extra packages.

Aptitude can tell you if a package was automatically installed to satisfy dependencies or if the user requested the install.  *aptitude search <pattern>* gives the package status with "A" indicating "Automatic".  I can't this facility in apt-cache.  Does anyone know where this information is stored?

I have used both synaptic and aptitude from the command line.  Should I expect any problems in mixing the two utilities?

---

