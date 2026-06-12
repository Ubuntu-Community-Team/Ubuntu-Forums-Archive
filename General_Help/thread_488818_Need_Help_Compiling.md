---
title: "Need Help Compiling"
date: 2007-06-30
forum: General Help
---

### Post by regomodo on 2007-06-30
Hi

I have just installed feisty server onto my T'pad and am now trying to install the drivers for a Ralink RT61 wifi card from serialmonkey. I know this works with a normal install but i cannot for the life of me get the package to compile correctly

I have 

$ tar -xvzf rt61.........tar.gz
$ cd ./Module

but when i go to do

$ sudo make

i get 
```

make: *** /lib/modules/2.6.20-15-server/build: No such file or directory. Stop.
rt61.ko failed to build!
make: *** [module] Error 1
```

I have installed the build-essential package and was shocked i had to install the make package after the server install.

Please help.What is causing this error?

---

### Post by regomodo on 2007-06-30
great, here we go again. another thread i make that gets effin nowhere

---

### Post by jrusso2 on 2007-06-30
Try to do configure before make and see if you get some error messages

---

### Post by regomodo on 2007-06-30
there is no need for configure, plus there is no configure file

it should be a straight

$ sudo make
$ sudo make install

presto!

but it isn't

---

### Post by regomodo on 2007-06-30
bump

---

