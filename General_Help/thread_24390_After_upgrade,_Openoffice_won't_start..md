---
title: "After upgrade, Openoffice won't start."
date: 2005-04-06
forum: General Help
---

### Post by Reb on 2005-04-06
Title says it all, I think.```
rob@here-be-dragons:~$ oo[anything here]
OpenOffice.org for Debian - see /usr/share/doc/openoffice.org/README.Debian.gz
running openoffice.org setup...
version already installed
ExitCode: 17
setup failed (code 0).. abort
---- Please read /usr/share/doc/openoffice.org/README.Debian.gz for known problems -----
```Any ideas?

---

### Post by Reb on 2005-04-06
To fix this problem did:```
rm -fr ~/.openoffice ~/.sversionrc
```And then I edited the ~/.sversionrc file from```
[Versions]
OpenOffice.org 1.1.3=file:///home/rob/.openoffice/1.1.4
```to```
[Versions]
OpenOffice.org 1.1.4=file:///home/rob/.openoffice/1.1.4
```

---

