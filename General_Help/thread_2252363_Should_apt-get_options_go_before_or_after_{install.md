---
title: "Should apt-get options go before or after {install remove autoremove}?"
date: 2014-11-11
forum: General Help
---

### Post by greg2lapa on 2014-11-11
sudo apt-get --purge autoremove cups-daemon
sudo apt-get autoremove --purge cups-daemon

Both the above commands seem to work. Am I correct to assume that the syntax used does not matter?

I wanted to check and see if there is a "right" way to syntax the above commands? Is it "better" to put --purge before or after autoremove?

---

### Post by bapoumba on 2014-11-11
The commands will be executed in the order you give them, ie first purges and then autoremoves cups-daemon, the second does it the other way around.
I'm not sure why you would autoremove a package (here cups-daemon) after purging it. The autoremove applies to the specified package in the command you ran. Basically, in your case, I would have used purge only.

If you want to autoremove all packages that were installed at some point as dependencies and are not needed anymore because you have removed the package that brought them along or for some other reason, use autoremove by itself.

---

### Post by greg2lapa on 2014-11-11
Does the order of execution make a difference? Say

sudo apt-get -y install exaile
sudo apt-get install -y exaile

or 

sudo apt-get --simulate install exaile
sudo apt-get install --simulate exaile

> **bapoumba said:**
> 
I'm not sure why you would autoremove a package (here cups-daemon) after  purging it. The autoremove applies to the specified package in the  command you ran. Basically, in your case, I would have used purge only.


Purging a package does not uninstall it, right? It just removes the configuration files. So if I've purged it, I still need to uninstall it (i.e., autoremove). am I understanding this wrong?

---

### Post by kc1di on 2014-11-11
Hi,

according to the help file which you can find by typing ```
apt-get --help
```
```
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

```

you can also get a more in-depth discussion by typing ```
man apt-get
```

---

### Post by Dennis N on 2014-11-11
**autoremove** is called a "command" in the man page and has no options (according to the man page). 

**--purge** is an option for **remove**, but **remove --purge** is the same as **purge** according to the man page.

I would do two commands separately, this way (with sudo):

**apt-get purge <package>**
**apt-get autoremove**

---

### Post by greg2lapa on 2014-11-11
> **kc1di said:**
> Hi,  according to the help file which you can find by typing ```
apt-get --help
``` ```
Usage: apt-get [options] command        apt-get [options] install|remove pkg1 [pkg2 ...]        apt-get [options] source pkg1 [pkg2 ...] 
```  you can also get a more in-depth discussion by typing ```
man apt-get
```  Thanks. What do  you advise with respect to "--purge" and "autoremove" as neither of these are listed as options. Is it better to run one before the other? Or should they not be used together?

---

### Post by bapoumba on 2014-11-11
Thanks Dennis N :)
```
sudo apt-get -s autoremove lubuntu-desktop
[sudo] password for bapoumba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv lubuntu-desktop [0.55]

```
autoremove actually removes when used with a package name.

---

### Post by philinux on 2014-11-11
@greg2lap 
Dennis N's post #5 has what you need.
And bapoumba's post #7

---

### Post by greg2lapa on 2014-11-11
Thx guys. to sum up for anyone else reading.  Proper syntax is to have the option before the source (apt-get -y install) except special cases like sudo apt-get remove --purge.  Autoremove has no options so it wouldn't work like remove in the sense sudo apt-get autoremove --purge. You need to run two commands.

---

### Post by Tadaen_Sylvermane on 2014-11-11
> **greg2lapa said:**
> Thx guys. to sum up for anyone else reading.  Proper syntax is to have the option before the source (apt-get -y install) except special cases like sudo apt-get remove --purge.  Autoremove has no options so it wouldn't work like remove in the sense sudo apt-get autoremove --purge. You need to run two commands.

First thing you should do before googling anything is check the man pages, in this case man apt-get. I know it's a small thing but I don't know where you got the idea that purge only removes config files. ```
apt-get purge (package)
``` removes the package, and the config files in one go.

---

### Post by deadflowr on 2014-11-11
It should be noted that purge will only remove the configuration files installed on the system, and not remove those configurations which will be in the user's home folder.

---

