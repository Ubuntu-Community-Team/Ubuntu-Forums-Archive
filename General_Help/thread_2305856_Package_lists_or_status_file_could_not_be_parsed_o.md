---
title: "Package lists or status file could not be parsed or opened"
date: 2015-12-09
forum: General Help
---

### Post by rewyllys on 2015-12-09
Today I upgraded my laptop from Linux Mint 17.2 to 17.3.  The update resulted in the Update Manager's reporting that "The package lists or status file could not be parsed or opened."


Googling the quoted statement led to a thread in the Ubuntu Forums ([http://ubuntuforums.org/showthread.php?t=2078996](http://ubuntuforums.org/showthread.php?t=2078996)) in which 2F4U suggested the following entries in the Terminal as a solution.


sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


I entered the suggested codes in my laptop's Terminal, and they solved the problem.

@2F4U, Many thanks.:popcorn:

BTW, the update to LM 17.3 went flawlessly for my desktop.

---

