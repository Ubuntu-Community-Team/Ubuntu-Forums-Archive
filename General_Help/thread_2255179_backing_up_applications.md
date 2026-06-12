---
title: "backing up applications"
date: 2014-12-02
forum: General Help
---

### Post by UncleMonty on 2014-12-02
Which available back up software, backs up the installed applications (as well as data) so when you transfer your data onto a new machine, you don't have to manually add spotify, chrome, dropbox, netflix, etc?

---

### Post by ian-weisser on 2014-12-02
Software Center has a 'sync between computers' feature for this purpose.

Backing up software for the purpose seems unnecessarily complicated. If you're using packages to keep your system up to date, then simply tell the new system to install the package. Terribly easy: sudo apt-get install spotify chrome nautilus-dropbox. Done. If you don't remember what you have installed...then do you really need it? Or just install it as you discover the need.

Do not restore package-installed files from a backup unless you also tell the package manager that the package is installed. Else you will quickly break your package manager and wind up reinstalling the packages anyway.

---

### Post by SeijiSensei on 2014-12-02
Alternatively, you can use the "get-selections" option in dpkg to create a list of installed packages on your current machine, then use the "set-selections" options on the new machine to install them all.  See [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages).

I always install from the repositories on new machines rather than trying to transfer an image of some sort.

---

### Post by gordintoronto on 2014-12-03
Everything you have installed or updated is in /var/cache/apt/archives unless you have run apt-get clean.

You could delete the old versions for which there has been an update, then copy the folder to your new computer and install each of the programs.

---

