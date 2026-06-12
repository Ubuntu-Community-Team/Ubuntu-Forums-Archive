---
title: "&quot;New software can't be installed because there is a problem with the current software"
date: 2015-02-22
forum: General Help
---

### Post by Thomas_Hankey on 2015-02-22
I am trying to install the graphics drivers for my two amd r7 250's and several other programs and I keep getting this.

```
installArchives() failed: Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
Error in function:
```

---

### Post by oldos2er on 2015-02-22
Are you using Ubuntu? If so, which version? Is this a new install? Have you successfully installed any packages using Software Center or apt-get?

---

### Post by Thomas_Hankey on 2015-02-22
Yes, 14.4.02, yes, yes

---

### Post by oldos2er on 2015-02-23
It might help if you could post the rest of the error message, if possible.

---

