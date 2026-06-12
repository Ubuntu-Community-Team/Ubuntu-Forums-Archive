---
title: "Synaptic"
date: 2007-12-11
forum: General Help
---

### Post by barbedsaber on 2007-12-11
I am having some problems with synaptic. it is somthing like, This pakege is dependent on some other pakage which is located at the end of the universe. I can't get stuff because of dependancies, mainly lib followed by somthing like audio. I tried finding the required files with firefox, but I can't. I am running 7.10 with all the updates, but I didn't have this problem with dapper. Can someone please tell me where to find another pakage manager, (other than synapptic) or a place where I can get most of the dependancy stuff. I havn't raced a penguine down a hill for almost a week now, I don't know how much longer I can take it!

---

### Post by Rocket2DMn on 2007-12-11
Have you enabled the universe repository?  Make sure that it's checked in System->Administration->Software Sources
If that doesn't work, try using apt-get from terminal
```
sudo apt-get update
sudo apt-get install foo
```
If it still gives you dependency problems, try
```
sudo apt-get update
sudo apt-get build-dep foo
sudo apt-get install foo
```
"foo" would be the name of the program.  If you have issues, please post the output of those commands.

---

### Post by as0l0 on 2007-12-11
i had something similar yesterday and i changed my software source from australian local server to main site (or something like that).  That fixed it for me.

---

### Post by barbedsaber on 2007-12-11
Thanks heaps guys, im downloading ppracer as we speak.

---

