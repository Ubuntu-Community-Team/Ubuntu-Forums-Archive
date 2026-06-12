---
title: "how to change PATH"
date: 2008-04-07
forum: General Help
---

### Post by lackofcreativity on 2008-04-07
I was installing a compiler for ARM to compile Rockbox, but I don't know how do do it. It says to add the directory "usr/local/arm-elf/bin" to my PATH. I know what it means and I know it has something to do with the .profile file, but upon looking at it with gedit, I can't figure out how to add the directory. How would I do this?

---

### Post by bodhi.zazen on 2008-04-07
```
gedit ~/.bash_profile
```

Add:

> source $HOME/.bashrc

Now, 

```
gedit ~/.bashrc
```

Add these lines at the bottom of the file :

> PATH=$PATH:usr/local/arm-elf/bin
export PATH

---

### Post by lackofcreativity on 2008-04-09
Hmmmmmmm... Doesn't seem to work. The folder exists and contains the command I want, but I can't just run the command from anywhere else and make it work.

---

### Post by bodhi.zazen on 2008-04-09
After you make the edit you need to either log off an back in or 

```
source ~/.bashrc
``` for the changes to take effect.

If you have done that, test it with

```
echo $PATH
```

---

### Post by lackofcreativity on 2008-04-10
echo $PATH returns that the right directory *is* included, but running applications in that folder (arm-elf-gcc) returns:
```
bash: arm-elf-gcc: command not found
```
I can run the actual app from its folder, but this just isn't an option because it is used for compiling. Thanks for your help!

---

### Post by lackofcreativity on 2008-04-10
Got it! I did it by doing...
```
export PATH=$PATH:/usr/local/arm-elf/bin
```
Thanks for all your help!

---

