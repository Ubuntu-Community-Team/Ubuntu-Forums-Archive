---
title: "dont know how to install .tar.bz2 files"
date: 2006-11-04
forum: General Help
---

### Post by UchihanoKonoha on 2006-11-04
I have come across a large array of files that use the .tar.bz2 type. so far i can only install .deb files. however i do not know how to install .tar.bz2 files. can someone help me please?

---

### Post by UchihanoKonoha on 2006-11-04
i realize i have to extract the files but what do i do after that?

---

### Post by Adramelech on 2006-11-04
I guess you downloaded source code?

---

### Post by UchihanoKonoha on 2006-11-04
well it has files and read me and all that. The read me keeps mentioning "Compiling" i dont know what that means. do i need any other software for this or just the terminal, if so what are the commands.

---

### Post by Adramelech on 2006-11-04
Read the readme file, the install and the documentation within the file, theres must exist indications on compiling your software.

Compiling is generating the binary files from the source code, if you are familiar with windows is like making a .cpp (source code) file into an .exe file.

The usual way to compile a program is to decompress the source code into a folder, open terminal and go to the path where the source code is, type

```

./configure
make
makeinstall

```

As you are compiling the source code, the program will not appear in synaptic as installed.

---

### Post by UchihanoKonoha on 2006-11-04
i cant locate the source code through terminal.

---

### Post by Adramelech on 2006-11-04
decompress it on a temp folder on your home directory.

```

cd ~
mkdir temp
cd temp
tar -jxvf myfilename.bz2
cd mynewfolder
./configure
make 
make install


```

---

### Post by taurus on 2006-11-04
> **Adramelech said:**
> decompress it on a temp folder on your home directory.

```

cd ~
mkdir temp
cd temp
tar -jxvf myfilename.bz2
cd mynewfolder
./configure
make 
make install


```
Actually, better make it

```

sudo make install
-or-
sudo make checkinstall

```
since you need to be root to install stuff to your system, except your $HOME...

---

### Post by UchihanoKonoha on 2006-11-04
ok im sorry this is all greek to me im gonna have to read how to use the terminal, im a complete newbie to this.

---

### Post by Blutack on 2006-11-04
You may need to install checkinstall and build-essentials first!
sudo apt-get install checkinstall build-essential

---

### Post by UchihanoKonoha on 2006-11-04
since i know nothing about terminal and i need a tutorial can anyone suggest where i could find one? Im completely new to this, the code you guys are giving me is not helping me i dont know if its that your code is complete or incomplete but its not running anything. if you are assuming that i know what to add with the particles of code you are giving me then you would be wrong. can someone direct me toward a good comprehensive learning text for this information.

---

### Post by taurus on 2006-11-04
I don't mean to sound hard on you but if you don't even know what a terminal is, then perhaps building something from source is a little over your head right now!  Try using synaptic/apt/aptitude to install then...

---

### Post by CatKiller on 2006-11-04
[This page]("http://monkeyblog.org/ubuntu/installing/") should give you some background on what you were trying to do, and other ways to do it.

---

### Post by UchihanoKonoha on 2006-11-06
thank you this will be very helpful for me in learning the different functions of linux.

---

