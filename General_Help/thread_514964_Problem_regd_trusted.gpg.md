---
title: "Problem regd trusted.gpg"
date: 2007-08-01
forum: General Help
---

### Post by vishzilla on 2007-08-01
Recently when i tried to update my system, I was getting an error "Could not download all repository indexes". I tried it through apt-get, i got the following error "Duplicate entries in sources.list".
I went to /etc/apt folder using the command line (i never edited or changed the sources.list). And i found there was a duplicate file of trusted.gpg "trusted.gpg~". So, I removed the "~ file"  from the folder. And it worked and the error was not displayed.  Why did it create a "~ file"?
Please help

---

