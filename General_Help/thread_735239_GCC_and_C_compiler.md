---
title: "GCC and C compiler"
date: 2008-03-25
forum: General Help
---

### Post by Geran on 2008-03-25
I keep getting the same error I try to install something using the "make" command.

checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Is there some package I'm missing?

---

### Post by mali2297 on 2008-03-25
Have you installed **build-essential**?

From the terminal,
```

sudo apt-get install build-essential

```
or use Synaptic.

EDIT:
What is the *something* that you want to install?

---

### Post by y-lee on 2008-03-25
hmmm do ya have buid-essentials installed ?

Be sure you have the universe and multiverse repositories enabled in synaptic and then open a terminal window and type in:

```
sudo apt-get install build-essential
```

Or use Synaptic and search for build-essential and install it.

---

### Post by seeker1458 on 2008-03-25
if your using apt-get you can always try this before installing any certian application.  Just checks to make sure you have everything you need.  Helped solved alot of looking for certian *lib files while upgrading to syslog-ng.  

```
sudo apt-get build-dep <package name here>

```
then

```
sudo apt-get install <package name here>
```


But if all you need is the compiler then the following will work fine.

```
sudo apt-get build-essential
```

---

### Post by Geran on 2008-03-25
Awesome, that hit the spot, thanks a lot guys.

---

