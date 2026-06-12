---
title: "Installing new version of Firefox"
date: 2008-05-19
forum: General Help
---

### Post by Robbyx on 2008-05-19
I have d/l and extracted the files from the rc1 release tarball. I am not clear how to install it. I assume I have to install with run-mozilla.sh which is one of the extracted files.  What is the syntax?

Robin

---

### Post by geraldm on 2008-05-19
Read the file README.txt in the top directory. 

OR
extract the tarball where you wish to keep the executables, then create a 
link in /usr/bin/firefox to the executable firefox in the top directory.
# which gives a quick and dirty, but useable executable.

Gerald

---

### Post by FakeOutdoorsman on 2008-05-19
[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

---

### Post by Robbyx on 2008-05-19
> **FakeOutdoorsman said:**
> [https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

I think I have read the rubric correctly in that the script only installs deb files. Am I correct?

Robin

---

### Post by Robbyx on 2008-05-19
> **geraldm said:**
> Read the file README.txt in the top directory. 

OR
extract the tarball where you wish to keep the executables, then create a 
link in /usr/bin/firefox to the executable firefox in the top directory.
# which gives a quick and dirty, but useable executable.

Gerald

Can you please give me an example as how to do this? I assume that my existing setup and bookmarks will still be accessed from their original location.

Robin

---

### Post by aysiu on 2008-05-19
> **Robbyx said:**
> I think I have read the rubric correctly in that the script only installs deb files. Am I correct?

Robin
Use the instructions for Manual Install (the .tar.gz file):
[https://help.ubuntu.com/community/FirefoxNewVersion#head-a18df3338b868ce5f14336fd2ee58ce6b5d574b2](https://help.ubuntu.com/community/FirefoxNewVersion#head-a18df3338b868ce5f14336fd2ee58ce6b5d574b2)

---

### Post by syxbit on 2008-05-19
likely there will be an update pretty soon.
they're taking their time though, as hardy is an already released LTS!
can't risk screwing stuff up

---

