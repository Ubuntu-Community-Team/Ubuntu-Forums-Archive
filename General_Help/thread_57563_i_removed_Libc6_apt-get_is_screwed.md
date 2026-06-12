---
title: "i removed Libc6 apt-get is screwed"
date: 2005-08-17
forum: General Help
---

### Post by Digitallysick on 2005-08-17
how do i reinstall all packages, i dont want to loose my files , anyway to just re install all packages? or maybe i could copy the bin folder from the cd and overwrite my current bin folder? i dont know what the solution would be i keep getting 

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6514 package `language-support-en':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by jasmuz on 2005-08-17
Why dont you mount the install CD, using a terminal go to the location of libc6 (/pool/l) and then just sudo dpkg -i packagename.deb 

I think that would be a quick fix

---

