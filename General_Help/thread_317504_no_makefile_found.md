---
title: "no makefile found"
date: 2006-12-12
forum: General Help
---

### Post by vanalex on 2006-12-12
Hello everybody! I'm new to Ubuntu and have a lot of problems but still i think that Ubuntu is meant to be the best operating system ever..
Here's one of my problems..everytime i compile a source i follow the procedure

./configure
make
sudo make install

the configure part is completed successfully but then when i type 'make' i get a message that 'there is no makefile found'. I already have installed the build-essential so...what's going wrong?
Thank you in advance for your help!

vanalex

---

### Post by hod139 on 2006-12-12
Does the ./configure command execute successfully or is there an error message?  If the configure script fails you won't get a makefile to run.

---

### Post by taurus on 2006-12-12
What's the output of 

```
ls -la
```

---

