---
title: "aurora themes look pants!"
date: 2008-05-03
forum: General Help
---

### Post by davbren on 2008-05-03
Hey, I've just installed aurora and I would like to use the themes, however, the themes look like crap (sorta like root does) how can I sort this?

---

### Post by BobCFC on 2008-05-03
You need to install the Aurora engine first before you can use the themes.  This requires a little more work than an ordinary theme it's not your fault.

First make sure you have the stuff needed to compile, paste or type this:

```
sudo apt-get install build-essential libgtk2.0-dev
```


Then right click on the zip file that you downloaded and choose Extract Here. This will give you two more zip files.. one is the engine the other are some themes.

Right click on aurora-1.4.tar.gz which is the engine zip file and extract that. Then open a terminal and browse to the folder such as
```

cd Downloads/aurora-1.4
```



Now  compile and install the engine (do each step one at a time):

```
./configure --prefix=/usr -enable-animation

make

sudo make install
```

---

