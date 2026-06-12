---
title: "after installing gimpshop, apt-get will not work"
date: 2006-11-15
forum: General Help
---

### Post by timmyblog on 2006-11-15
I attempted to install gimpshop from plastic bugs and was not able to get that package working so I grabbed a ubuntu specific package and as it turns out the install worked just fine. I have ran the software perfectly with no problems.

Now a few hours later I try to upgrade some other packages and my synaptic won't work. It gives me an error, and even after running apt-get update which works fine I still am unable to run automatic updates and/or install new packages. Here is the error:

E: The package gimpshop needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

apt-get remove gimpshop returns the same error. Any ideas as to what this could be?

---

### Post by PartickThistle on 2006-11-16
I assume the package you installed has some conflicting libs.

I'd recommend;

apt-get install -f

Then reinstalling from source using --prefix=/to/your/home/dir

---

### Post by timmyblog on 2006-11-16
apt-get -f install returns the same error

what would i use the other command on? Do I have to go and track down that package?

---

### Post by timmyblog on 2006-11-16
rather apt-get install -f returns an error

---

### Post by organica on 2006-11-16
I'm guessing its a broken package?  Try Synaptic Package Manager and choose broken in the left column.  Anything show up?

---

### Post by PartickThistle on 2006-11-16
Can you post the full error?

---

### Post by timmyblog on 2006-11-16
WHen opening up the synaptic package manager I immediately get this error:

E: The package gimpshop needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by timmyblog on 2006-11-16
WHen selecting broken in the left column no packages show up.

I might also add that after closing that initial error message there are no packages showing up at all.

---

### Post by PartickThistle on 2006-11-16
Try;

sudo dpkg -r gimpshop

If that errors, try;

sudo dpkg --force -r gimpshop

---

### Post by timmyblog on 2006-11-16
tim@tim-laptop:~$ sudo dpkg -r gimpshop
Password:
dpkg: error processing gimpshop (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gimpshop
tim@tim-laptop:~$ sudo dpkg --force -r gimpshop
dpkg: unknown force/refuse option `-r'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


That's the output from those two commands.

---

### Post by blackbeastofaarrgh on 2006-11-17
This is risky, but it's worked for me many times: you could always edit /var/lib/dpkg/status. (BACKUP first!!) Search for "gimpshop", find the entry and remove it.
Again, do at your own risk. But it *has* worked for me.

---

### Post by timmyblog on 2006-11-17
That seemed to have fixed it, thanks.

---

