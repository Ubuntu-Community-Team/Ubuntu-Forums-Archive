---
title: "compling amsn from svn, making a deb of it and installing?"
date: 2007-11-28
forum: General Help
---

### Post by ELD on 2007-11-28
Can anyone help me do that or point me to the right place? Thanks!

---

### Post by x2fast on 2007-11-28
open terminal....

sudo apt-get install amsn

---

### Post by ELD on 2007-11-28
Did you even bother to read the title of the post?

Before trying to be helpful, read first.

---

### Post by x2fast on 2007-11-28
Haha, oops completely disregard my post, and please...you know where you can put it.

Thanks!   :)

---

### Post by omegamike3 on 2007-11-28
wow, even i feel awkward now...

---

### Post by Bananas21ca on 2007-11-28
You can get the latest SVN snapshot from:
[http://www.amsn-project.net/download.php]("http://www.amsn-project.net/download.php")
It was updated today so its not old or anything.
Follow the instructions in the install file to compile.

As for making it a .deb file I have no idea

Edit: Actually looking at the install file it has a option "make deb". That should be what your looking for

---

### Post by ELD on 2007-11-29
You know i looked in the readme file, but not the install file, haha, oops, nice one will give it a go now :)

I tried to make a deb from it and got this:
> 
liam@liam-desktop:~/Desktop/msn$ make deb
mkdir -p ./distrib/DEB
sed "s/#VERSION#/0.97b-svn`which svnversion > /dev/null && svnversion`/" debian/changelog.in > debian/changelog
fakeroot debian/rules clean
make: fakeroot: Command not found
make: *** [deb] Error 127


Any ideas?

Thanks.

---

