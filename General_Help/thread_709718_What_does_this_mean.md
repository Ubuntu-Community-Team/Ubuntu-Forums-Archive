---
title: "What does this mean?"
date: 2008-02-27
forum: General Help
---

### Post by banjopikker on 2008-02-27
Can't find public key. I get this error when I try to update installed apps.

---

### Post by Nameless_one on 2008-02-27
This probably appears when you try to update an application which is on a repository not related to Ubuntu. Have you added a repository to your sources.list from a webpage? If so, in that webpage, there is probably a PGP key you need to add to the database of apt-get's keys. so that the packages from the repository can be authenticated. Check the webpage for instructions on adding their repository to your sources, and there will probably be an instruction like this one there: 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - (EXAMPLE)
```

Run that instruction in a terminal.

---

