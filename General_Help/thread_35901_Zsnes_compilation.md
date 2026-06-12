---
title: "Zsnes compilation"
date: 2005-05-20
forum: General Help
---

### Post by Tails747 on 2005-05-20
I'm trying to compile Zsnes for myself. I've gotten as far as navigating to the source directory, and typing "./configure", but I get this returned:

> checking build system type... configure: error: connot guess build type; you must specify one

I'm guessing I need to specify the build type somehow?

how is this done?

---

### Post by Xian on 2005-05-20
[QUOTE=Tails747]I'm guessing I need to specify the build type somehow?

how is this done?[/QUOTE]
Try this command:

```
./configure --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu --
build=i686-pc-linux-gnu
```

---

### Post by Tails747 on 2005-05-20
I just tried that, and I got this:

> nu --target=i686-pc-linux-gnu --build=i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for i686-pc-linux-gnu-gcc... no
checking for gcc... no
checking for i686-pc-linux-gnu-cc... no
checking for cc... no
checking for cc... no
checking for i686-pc-linux-gnu-cl... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Do I need to install/enable a compiling device of some sort? o_O

---

### Post by bored2k on 2005-05-20
[QUOTE=Tails747]I just tried that, and I got this:



Do I need to install/enable a compiling device of some sort? o_O[/QUOTE]
 sudo apt-get install build-essential

---

### Post by Tails747 on 2005-05-21
Never mind, I've managed to download it using synaptic.. now sound isn't working.. I know this has been awnsered here before, so I'm going to take a look around. :P

---

### Post by Xian on 2005-05-21
You really should go ahead an install that build-essential package.
There will come another time when it will be needed.

---

### Post by Tails747 on 2005-05-21
Okay, I've installed that package.

Also, I've found out that making a launcher with the command 'sudo zsnes' starts the program with sound. However, if I put this launcher as a button on the upper panel and use it, there is no sound support. Do I have to use the launcher on the desktop for sound support, or is there a workaround?

---

### Post by Xian on 2005-05-21
[QUOTE=Tails747]Okay, I've installed that package.

Also, I've found out that making a launcher with the command 'sudo zsnes' starts the program with sound. However, if I put this launcher as a button on the upper panel and use it, there is no sound support. Do I have to use the launcher on the desktop for sound support, or is there a workaround?[/QUOTE]
Try instructing the launcher to "Run In Terminal".
Just tick that box in the create launcher menu.

---

