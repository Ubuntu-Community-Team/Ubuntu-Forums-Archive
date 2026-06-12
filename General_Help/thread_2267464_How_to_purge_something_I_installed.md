---
title: "How to purge something I installed"
date: 2015-03-01
forum: General Help
---

### Post by michael-piziak on 2015-03-01
I installed a PPA that didn't completely work for me.

What do I type into terminal to purge it (complete un-install).  I think I need to install purge program first don't I ?

This is what I typed to install it:

sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder
sudo apt-get update
sudo apt-get install simplescreenrecorder

---

### Post by v3.xx on 2015-03-01
I like ppa-purge for this.

[http://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](http://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)

---

### Post by michael-piziak on 2015-03-01
> **v3.xx said:**
> I like ppa-purge for this.

[http://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](http://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)


ok, to install that I type this into terminal first, right ? 

**sudo apt-get install ppa-purge**

Then exactly what would I type to purge the program I installed.

**sudo ppa-purge ___________?______________**

---

### Post by v3.xx on 2015-03-01
sudo ppa-purge ppa:maarten-baert/simplescreenrecorder

---

### Post by deadflowr on 2015-03-01
ppa-purge is best used for when you tried upgrading an existing package.
Say you tried libreoffice 4.4, and decided to revert back to it.
ppa-purge will remove the ppa and then revert the packages back to what was installed before the ppa was added, if that makes sense.

If, however, you added  a new package altogether, you would probably be better off running
```
sudo apt-get purge packagename
```
and adding a --remove option to the add-apt-repo command
```
sudo add-apt-repository --remove ppa/name/
```

---

### Post by v3.xx on 2015-03-01
> ppa-purge will remove the ppa and then revert the packages
Yes it is overkill, but still nice just to use one package for all.

---

### Post by michael-piziak on 2015-03-01
> **deadflowr said:**
> ppa-purge is best used for when you tried upgrading an existing package.
Say you tried libreoffice 4.4, and decided to revert back to it.
ppa-purge will remove the ppa and then revert the packages back to what was installed before the ppa was added, if that makes sense.

If, however, you added  a new package altogether, you would probably be better off running
```
sudo apt-get purge packagename
```
and adding a --remove option to the add-apt-repo command
```
sudo add-apt-repository --remove ppa/name/
```

ok, so in my case I type 

[COLOR=#000000]sudo apt-get purge ppa:maarten-baert/simplescreenrecorder

[/COLOR]then type

[COLOR=#000000]sudo add-apt-repository --remove ppa:maarten-baert/simplescreenrecorder[/COLOR]



right ?

---

### Post by deadflowr on 2015-03-01
no, the package name is simplescreenrecorder
the ppa is ppa:maarten-baret/simplescreenrecorder.

But as a sidenote, since simplescreenrecorder installs two packages
simplescreenrecorder and simplescreenrecoder-lib
try adding a * to the end to remove both packages at once.
```
sudo apt-get purge simplescreenrecorder*
```
after you purge the actual package, you can remove the ppa.
(But I actually do not think the order of removal is important, whether you remove the package first or the ppa,
but I tend to remove the package, then flush the ppa down the toliet)
After you remove the ppa, run the apt-get update command to refresh the system.
(Running the apt-get update command can also show you that you successfully removed the ppa, and/or show you any problems, if any)

---

### Post by michael-piziak on 2015-03-01
> **deadflowr said:**
> no, the package name is simplescreenrecorder
the ppa is ppa:maarten-baret/simplescreenrecorder.

But as a sidenote, since simplescreenrecorder installs two packages
simplescreenrecorder and simplescreenrecoder-lib
try adding a * to the end to remove both packages at once.
```
sudo apt-get purge simplescreenrecorder*
```
after you purge the actual package, you can remove the ppa.
(But I actually do not think the order of removal is important, whether you remove the package first or the ppa,
but I tend to remove the package, then flush the ppa down the toliet)
After you remove the ppa, run the apt-get update command to refresh the system.
(Running the apt-get update command can also show you that you successfully removed the ppa, and/or show you any problems, if any)

ok so I type into terminal:  sudo apt-get purge simplescreenrecorder*

then I type into terminal:

[COLOR=#000000]sudo add-apt-repository --remove ppa:maarten-baert/simplescreenrecorder

then type in:  [/COLOR][FONT=Ubuntu Mono]sudo apt-get update[/FONT][COLOR=#000000]


right?[/COLOR]

---

### Post by deadflowr on 2015-03-01
> **michael-piziak said:**
> ok so I type into terminal:  sudo apt-get purge simplescreenrecorder*

then I type into terminal:

[COLOR=#000000]sudo add-apt-repository --remove ppa:maarten-baert/simplescreenrecorder

then type in:  [/COLOR][FONT=Ubuntu Mono]sudo apt-get update[/FONT][COLOR=#000000]


right?[/COLOR]

Yep.

Also, for fun you can do a dry-run of the purge command by adding a -s flag.
 sudo apt-get purge -s simplescreenrecorder* 
This will show you exactly what will happen, but not actually do it.
So you can be sure of the outcome.
-s = simulate, can also by spelled out --simulate

---

### Post by michael-piziak on 2015-03-01
Thanks to both of you.

Marking this thread as solved.

---

### Post by michael-piziak on 2015-03-01
One additional question:

What's the difference in doing this in terminal and removing it in the software center ?

---

### Post by CantankRus on 2015-03-01
From "man apt-get" 
```
**purge**
purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).
```

So **sudo apt-get purge [COLOR="#696969"]<package>[/COLOR]** removes the package and any config files.

Usually if you have added an application from a third party ppa and no longer want that package you 
would run....
```
sudo ppa-purge ppa:[COLOR="#696969"]<ppausername>/<ppaname>[/COLOR]
```
Which will remove/downgrade packages you have installed from this ppa.
It only disables the ppa, so it can be re-enabled if you desire at a later date using the software sources dialog.
[ATTACH=CONFIG]260373[/ATTACH]
If the package you installed has a version in the official repositories it will revert to these official packages.
eg running... 
```
sudo ppa-purge ppa:maarten-baert/simplescreenrecorder
```
will remove the two packages in this ppa because these packages are not in the official repositories.
You would not run ppa-purge if the ppa contains other packages you want to keep.

In some cases you may have added a third party ppa to upgrade a particular buggy application that's in the official repositories
but find the upgrade is worse than before.
You now want to go back to the package version you had before.
In this case running ppa-purge will revert the packages to the official versions and disable the third party ppa.

If you are inclined to use third party ppas I would install **synaptic** and use this rather than the software centre.
Using  third party ppas requires a bit more care on your behalf in checking what's in the ppas.
[ATTACH=CONFIG]260375[/ATTACH]

Here's a link on using ppa-purge..... [http://ubuntuforums.org/showthread.php?t=2264416&p=13224880#post13224880](http://ubuntuforums.org/showthread.php?t=2264416&p=13224880#post13224880)

---

