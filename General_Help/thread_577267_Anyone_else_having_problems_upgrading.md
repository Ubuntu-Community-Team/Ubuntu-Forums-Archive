---
title: "Anyone else having problems upgrading?"
date: 2007-10-16
forum: General Help
---

### Post by Tlon on 2007-10-16
While trying to install tonight's batch of patches....

Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 118637 files and directories currently installed.)
Preparing to replace audacious-plugins 1.3.5-3ubuntu2 (using .../audacious-plugins_1.3.5-3ubuntu4_i386.deb) ...
Unpacking replacement audacious-plugins ...
dpkg: error processing /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/audacious/General/libcurl.so', which is also in package audacious-plugins-extra
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
m@e:~$

Anyone know why this is happening?

---

### Post by jocko on 2007-10-16
> **Tlon said:**
> 
Preparing to replace audacious-plugins 1.3.5-3ubuntu2 (using .../audacious-plugins_1.3.5-3ubuntu4_i386.deb) ...
Unpacking replacement audacious-plugins ...
dpkg: error processing /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/audacious/General/libcurl.so', which is also in package audacious-plugins-extra


I got the same. I solved it by first completely removing audacious-plugins-extra. 
Then I updated audacious-plugins and the rest of the updates, and finally I re-installed audacious-plugins-extra.

---

### Post by taavi on 2007-10-16
Same here. I could remove audacious-plugins-extra, but why this libcurl.so is dublicated in both packages?

---

### Post by jocko on 2007-10-16
In the changelog it said something about a file move, so I guess someone decided to move a file from -plugins-extra to -plugins, which caused a conflict between the old version of -plugins-extra and the new version of -plugins.

---

