---
title: "Have a broken package, am nervous about reinstalling"
date: 2007-01-11
forum: General Help
---

### Post by stopsatgreen on 2007-01-11
Synaptic reports that I have a broken package: libfontconfig-1; when I mark it for reinstallation, I get the message that as part of the process a whole bunch of packages need to be removed - most of my most important packages!

I don't want to go ahead and remove them all; is there any way to fix this without the mass removal? Or will it all be reinstalled automatically? I could really do with some guidance!

---

### Post by stopsatgreen on 2007-01-11
Bump... would really appreciate a response on this.

---

### Post by stopsatgreen on 2007-01-11
Please help... I don't want to shutdown without resolving this problem!

---

### Post by stopsatgreen on 2007-01-12
Fixed! I decided to get my hands dirty with the command line;

1. Ran sudo apt-get -f install, which informed me that:

```
The following packages have unmet dependencies.
libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.1-2 is to be installed
```

2. Ran sudo apt-get -f install fontconfig-config=2.3.2-7ubuntu2, which downgraded the broken package and fixed the problem.

Phew!

---

### Post by dcstar on 2007-01-13
> **stopsatgreen said:**
> Fixed! I decided to get my hands dirty with the command line;

1. Ran sudo apt-get -f install, which informed me that:

```
The following packages have unmet dependencies.
libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.1-2 is to be installed
```

2. Ran sudo apt-get -f install fontconfig-config=2.3.2-7ubuntu2, which downgraded the broken package and fixed the problem.

Phew!

You could have achieved the same thing in Synaptic by selecting the package and using the "Force Version" option.

---

### Post by stopsatgreen on 2007-01-13
If only it were that easy; the option wasn't available to me in Synaptic.

---

