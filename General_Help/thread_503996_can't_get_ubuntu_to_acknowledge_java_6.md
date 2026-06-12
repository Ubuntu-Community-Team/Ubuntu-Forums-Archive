---
title: "can't get ubuntu to acknowledge java 6"
date: 2007-07-18
forum: General Help
---

### Post by sirana on 2007-07-18
I'm not able to get ubuntu to acknowledge that i have java 6.

I can install it alright and it shows in synaptic, but "java -version" still gets me the following message:

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

complete purge and reinstall doesn't help.
Same thing with java 5. 

java 1.4 works fine.

any thoughts?




Holger

don't bite me, i'm a linux newbie

---

### Post by firebadger on 2007-07-18
sudo update-alternatives --config java

---

### Post by sirana on 2007-07-18
wow thanks, that was easy.

now i feel stupid...

thanks again....

holger

---

### Post by firebadger on 2007-07-18
No problem - it's hardly intuitive! :)

---

