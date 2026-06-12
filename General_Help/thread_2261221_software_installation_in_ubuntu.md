---
title: "software installation in ubuntu"
date: 2015-01-17
forum: General Help
---

### Post by pankaj_kumar2 on 2015-01-17
plese give the steps for installing .tar and .deb file...from command prompt. and tell me about what pakages are required for installing the software.

---

### Post by Bucky Ball on 2015-01-17
*Thread moved to **General Help**.*

Welcome. Doing a search before posting is a good idea. For .deb files, double click the file. For .tar files, [this]("http://en.kioskea.net/forum/affich-107338-how-to-install-tar-gz-file-on-ubuntu") might help. Post back if you have issues. Good luck.

---

### Post by Mark Phelps on 2015-01-17
> tell me about what pakages are required for installing the software.

Every app has its own packages, there is not one universal set.

When you go to install a .deb file, it will tell you what dependencies are needed. This is more work than using the Software Center -- which is what you should use.

When you go to install from a .tar file, generally, since this is source, the stuff is included.  But generally, there is a configure file you execute first that looks to see if you have all the dependencies installed.  This is the HARDEST way to install anything and involves a LOT more work than simply using the Software Center.

---

### Post by trag on 2015-01-20
If im dealing with Tar.gz file I prefer to convert it into a one click install .deb file using alien. if your interested in going this way try this.
sudo apt-get install alien
from terminal follow these steps

[FONT=Roboto Slab] Type it the way you see it(there is a space after sudo, after alien and one after deb too)[/FONT]

[FONT=Roboto Slab]sudo alien --to-deb ~/Downloads/mintygoodness.tgz[/FONT]


[FONT=Roboto Slab]Then hit enter and enter your password if prompted and enter again.[/FONT]
[FONT=Roboto Slab]Then you will have a nifty little .deb file. All you have to do is find it. Mine sometimes end up on the desktop and sometimes in my Home Folder (at the end). Once you find it, click on it to open and it will automatically run with gdebi package installer, which will install the package for you. All done![/FONT]

---

