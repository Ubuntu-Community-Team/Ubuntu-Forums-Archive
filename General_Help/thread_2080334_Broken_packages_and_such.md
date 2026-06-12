---
title: "Broken packages and such"
date: 2012-11-03
forum: General Help
---

### Post by Lindenk on 2012-11-03
I'm currently trying to install monodevelop-latest from this ppa ppa:keks9n/monodevelop-latest ([https://launchpad.net/~keks9n/+archive/monodevelop-latest](https://launchpad.net/~keks9n/+archive/monodevelop-latest)) and am recieving the following error. I'm running Ubuntu 12.10 64 bit.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 monodevelop-latest : Depends: gtk-sharp2 (= 2.12.10-9ppa) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Normally I would figure installing gtk-sharp2 would fix it but it depends on another version of it that I expected to be in the above repository. I also haven't found it by googling.

Please help.

---

### Post by ibjsb4 on 2012-11-03
The following **unsupported** and          **untrusted** Personal Archives (PPAs) provide          packages of          'gtk-sharp2':
                    [                        [IMG]https://launchpad.net/@@/ppa-icon[/IMG]                        MonoDevelop 3.0 + HUD support PPA             ]("https://launchpad.net/%7Ekeks9n/+archive/monodevelop-latest") owned by             [Nikita Tsukanov]("https://launchpad.net/%7Ekeks9n")                        Versions:             Natty (2.12.10-9ppa), Oneiric (2.12.10-9ppa), Precise (2.12.10-9ppa) 

Looks like it has not yet been updated for 12.10

[https://launchpad.net/ubuntu/+source/gtk-sharp2](https://launchpad.net/ubuntu/+source/gtk-sharp2)

---

### Post by Lindenk on 2012-11-03
Oh well, thank you anyway.

---

### Post by Bashing-om on 2012-11-03
apt-cache show => has the version 2.12.10 -2ubuntu4 available in the 12.04 repository.

```
apt-cache show gtk-sharp2
```can not see that it will hurt any more to try and install it ???
[INDENT]just try'n to help < == BDQ

[/INDENT]

---

