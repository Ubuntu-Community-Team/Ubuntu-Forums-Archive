---
title: "How to install movie/film collection manager Griffith in Ubuntu 18.04?"
date: 2018-06-10
forum: General Help
---

### Post by tellapu on 2018-06-10
Griffith is not the regular Ubuntu repositories/package list anymore (Ubuntu 18.04). I tried to install the deb.file from this launchpad page but I get errors:
"W: griffith: package-installs-into-obsolete-dir etc/bash_completion.d/ : ^etc/bash_completion.d/ -> usr/share/bash-completion/completions Ensure new filename matches sticter requirements (see [https://bugs.debian.org/776954](https://bugs.debian.org/776954) and [https://bugs.debian.org/814599](https://bugs.debian.org/814599))
W: griffith: package-installs-into-obsolete-dir etc/bash_completion.d/griffith : ^etc/bash_completion.d/ -> usr/share/bash-completion/completions Ensure new filename matches sticter requirements (see [https://bugs.debian.org/776954](https://bugs.debian.org/776954) and [https://bugs.debian.org/814599](https://bugs.debian.org/814599))
W: griffith: command-in-menu-file-and-desktop-file griffith usr/share/menu/griffith:7
Lintian finished with exit status 0"
 AND
 "Error: Dependency is not satisfiable: python-imaging (>= 1.15-6)"
 Any tips how to install this in Ubuntu 18.04?
Or any alternative for Ubuntu as development of this great tool seems to be halted?

---

### Post by Frogs Hair on 2018-06-10
From what I find is Griffith reached EOL about 2012 or so. Even the forum and Google groups are defunct and the package you need is unavailable from official sources. You could look into [this]("http://www.gcstar.org/index.en.php") project being the only Linux alternative I've found so far.

Edit: I find the download link to be Broken for [GCstar]("http://wiki.gcstar.org/en/install#download_gcstar_sources") . 

Edit: [Data Crow]("http://www.datacrow.net") might be worth a look and it has a working download.

---

### Post by tellapu on 2018-06-16
Thank you for the tips!
It is a pity Griffith is dead :( .

---

### Post by vanadium on 2018-06-17
gcstar is still in the Ubuntu repositories: you can install it with "sudo apt install gcstar". For reasons I do not understand, it does not show up in Software.

---

### Post by tellapu on 2018-06-18
@vanadium Thank you! "sudo apt install gcstar" is what I did.   
GCstar nicely imports the exported Griffith database but the fetching of information from the online databases for new movies is not yet satisfactory (lacking a lot of info), we will see.

---

