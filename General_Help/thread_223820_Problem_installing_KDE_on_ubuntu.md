---
title: "Problem installing KDE on ubuntu"
date: 2006-07-27
forum: General Help
---

### Post by Unknowndeepness on 2006-07-27
Hello there!

I'm trying to install KDE on ubuntu, but i allways get errors. This is what happends:

```

deep@inject:~$ sudo apt-get install kde
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kdegraphics but it is not going to be installed
       Depends: kdesdk but it is not going to be installed
E: Broken packages

```

I saw in some thread here to do this:
```

deep@inject:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdegraphics-kfile-plugins but it is not going to be installed
E: Broken packages

```

Errors aswell.

How can i get KDE?

---

### Post by aysiu on 2006-07-27
[This](http://www.ubuntuforums.org/showpost.php?p=1304491&postcount=3) should help you.

---

