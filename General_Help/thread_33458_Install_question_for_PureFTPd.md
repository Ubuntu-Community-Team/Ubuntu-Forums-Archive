---
title: "Install question for PureFTPd"
date: 2005-05-11
forum: General Help
---

### Post by Unununium on 2005-05-11
I am trying to install PureFTPd and I am having trouble with the install directions.  As with most installs that I have attempted lately, they say to type: ./configure and then type 'make' and so on.  Whenever I try to use this command it never seems to work.  I am a newbie, so please explain in detail what I am not understanding or what I need to do.  As for the pure ftpd it says to type ./configure which I have done.  Next, it says to type 'make install-strip' however I get the following error: make: *** No rule to make target `install-strip'.  Stop.

I have no idea what this means or what to try.  Can someone give me some direction?  Thanks!!!

---

### Post by tread on 2005-05-11
Unix programs are usually built in three steps:

1. ./configure: generates a new Makefile
2. make: compiles the program/software
3. sudo make install: installs the program. sudo is required since usually you do not have permission to write to the installation directory.

In your case, make install-strip probably refers to a rule to strip the binaries of debugging symbols to make them smaller in size, the principle is still the same as above.

You are getting a Makefile not found error, which means ./configure failed for some reason. Could you post the output of ./configure?

---

### Post by tread on 2005-05-11
Hang on, you've said "no rule to make install-strip".

Try the 3 standard steps:

./configure
make 
sudo make install

---

### Post by Unununium on 2005-05-14
Thanks.  I didn't have a C compiler installed yet, so I did the following...

sudo apt-get -f install gcc

then:
sudo apt-get -f install g++

I tried your commands and everything seemed to install correctly.

Thanks again

---

