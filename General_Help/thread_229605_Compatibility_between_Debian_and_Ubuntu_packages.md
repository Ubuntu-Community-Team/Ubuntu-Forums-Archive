---
title: "Compatibility between Debian and Ubuntu packages?"
date: 2006-08-04
forum: General Help
---

### Post by DC@DR on 2006-08-04
Hi Ubuntu users,

I'm a n00b with Ubuntu (started using it for around 3 months), and very happy with Ubuntu so far. Yesterday I tried to using a Debian .deb package to install in Ubuntu, and found out that it didn't work with Ubuntu. As I knew that Ubuntu is a fork from Debian GNU/Linux distro, I just wondered why the Debian packages dont work well in Ubuntu? Is there any incompatibility here? And is there any way to make them compatible? Please help me with this...Many tks in advance :-)

---

### Post by 5-HT on 2006-08-04
Yup, unfortunately Debian and Ubuntu do not share binary compatibility. While some packages from one distro may function properly on the other, a lot will not and it is not recommended to mix and match. Is the package available in Ubuntu's repositories? If not, compiling may be the easiest option.

---

### Post by zxee on 2006-08-04
What you've described is not always the case.Some deb packages do work with ubuntu but there is the issue of dependencies i.e the fork being different/altered from what it came from.
The best way IMO to get help with this is to let us know what package you're trying to install-chances are someone will have had experiance with it.

---

### Post by em3raldxiii on 2006-08-04
I have used the program ''Alien'' to make RPM binaries usable in Ubuntu, is it possible that this would also work for pure .DEB packages?

---

### Post by Jagot on 2006-08-04
> **em3raldxiii said:**
> I have used the program ''Alien'' to make RPM binaries usable in Ubuntu, is it possible that this would also work for pure .DEB packages?

Nope - not for other Debs.  Only for LSB, Red Hat, Stampede and Slackware Packages.

---

### Post by em3raldxiii on 2006-08-05
That seems mighty peculiar.  You'd think they'd make some kind of effort to maintain a certain amount of backwards-compatability.  I mean, why should it be easier to install RPMs?

---

