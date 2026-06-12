---
title: "Hardy medibuntu repo yet?"
date: 2008-04-27
forum: General Help
---

### Post by danbuter on 2008-04-27
I was using the Gutsy medibuntu repo. Is there a Hardy one now, and if so, how do I get it via terminal?

---

### Post by thrice upon a time on 2008-04-27
To set up the repo:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

To get the key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Accept the key, which it will download, and you're set ;-)

Wiki page can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by danbuter on 2008-04-27
medibuntu-keyring does not exist.

---

### Post by danbuter on 2008-04-27
Maybe I should rephrase that: I tried to download medibuntu-keyring and aptitude said it could not be found. And I have not been able to get anything from the medibuntu repo, even though it is added (as per the first suggested command).

---

### Post by thrice upon a time on 2008-04-28
Have you tried the instructions on the wiki page? Medibuntu keyring does indeed exist ;)

---

