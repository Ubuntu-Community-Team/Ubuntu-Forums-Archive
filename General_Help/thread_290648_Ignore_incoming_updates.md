---
title: "Ignore incoming updates?"
date: 2006-11-01
forum: General Help
---

### Post by Ghazgkull on 2006-11-01
Every time I start up my computer, I get notified of updates for the wine and libwine packages which I do not want to install. Is there any way that I can tell the update manager to stop asking me to upgrade certain packages?

---

### Post by Beaucephus on 2006-11-01
I believe you can "freeze" a version in the synaptic package manager.  Search for the packages in question and right click on them for options.

---

### Post by RjBanker18 on 2006-11-01
There unfortunately there is no freeze option (might be nice though).  But since you might not want those anyway...you can just remove them.  Just use those names you have and goto
System>Synaptic Package manager
Put in your root password
Hit "Ctrl+F" and search the name
Right-click the package with that name and click "Remove"
I suggest removing wine first.
:EDIT: This is probably not the best way but...If you are looking to keep the wine packages, like using Synaptic Package manager to update, and want the update manager to stop bothering you completely.  Then I would say you can just remove the "update-manager" package if it is annoying you! :P

---

### Post by krismatth3 on 2006-11-01
RjBanker18, I have this same problem  and I suspect he doesn't want to remove wine. I have a slightly older version of wine, compiled with patches for running World of Warcraft.

My solution has been to kill the update manager - don't want it, I update with apt-get anyway.

---

### Post by Ramses de Norre on 2006-11-01
There certainly is a freeze option, select the package and then there is a package menu I think and I think there is an option "lock version" or something like that.

I'm not sure about the names but it's something like that.

---

### Post by digby on 2006-11-01
If you look at [this page ]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html")(section 3.10) it will tell you all about pinning packages so that apt will not update them.  It's mostly just a matter of editing your /etc/apt/preferences file.

---

### Post by Ghazgkull on 2006-11-01
> **Ramses de Norre said:**
> There certainly is a freeze option, select the package and then there is a package menu I think and I think there is an option "lock version" or something like that.

Awesome, thanks. The "Lock Version" action is, in fact, in the "Package" menu which appears on the top toolbar of the package manager. This is exactly what I was looking for.

Now I can use the update manager without constantly being prompted to update these packages. (yes, I need to keep an old version of wine installed for a specific app)

---

### Post by matoxxx on 2006-11-01
use *aptitude hold* command in terminal for *holding* packages at their current version

remove, purge, hold, keep, reinstall
              These commands are the same as ‘‘install’’, but apply the named
              action to all packages given on the command line for which it s
              not overridden. The difference between hold  and  keep  is that
              hold  will  cause a package to be ignored by future upgrade om&#8208;
              mands, while keep merely cancels any scheduled  actions  on  he
              package.

---

