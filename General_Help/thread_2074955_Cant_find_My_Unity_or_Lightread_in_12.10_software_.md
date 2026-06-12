---
title: "Cant find My Unity or Lightread in 12.10 software centre?"
date: 2012-10-22
forum: General Help
---

### Post by fixles on 2012-10-22
Cant find My Unity or Lightread in 12.10 software centre?  Just did a fresh install of 12.10 and cant find either of the above. Are they still porting software to 12.10 or do I need to enable something?  I have all 4 sources ticked in software sources and ran a apt-get update but still cant find either.  Thanks.

---

### Post by vasa1 on 2012-10-22
Don't know about Lightread but My Unity has been removed. Something about "gambas" ...
[http://askubuntu.com/questions/203709/how-do-i-install-myunity-on-12-10](http://askubuntu.com/questions/203709/how-do-i-install-myunity-on-12-10)

---

### Post by MorrisseyJ on 2012-12-23
Solution is here:

[http://askubuntu.com/questions/202064/unable-to-locate-package-lightread](http://askubuntu.com/questions/202064/unable-to-locate-package-lightread)

Add ppa:cooperjona/lightread

In the terminal:

> sudo add-apt-repository ppa:cooperjona/lightread
sudo apt-get update
sudo apt-get install lightread

j

---

