---
title: "Has Anyone Installed Gaim2.0.0 Beta?"
date: 2006-09-07
forum: General Help
---

### Post by Mark76 on 2006-09-07
If so, HELP :oops:

---

### Post by skymt on 2006-09-07
How can I help you?

---

### Post by kerry_s on 2006-09-07
Yep, i use it. Add this to your /etc/apt/sources.list->

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

---

### Post by Mark76 on 2006-09-07
My what!?

---

### Post by Senshi on 2006-09-07
What is it that you actually need help doing?

---

### Post by Mark76 on 2006-09-07
Installing it, so I can take a look.

I downloaded the tar.gz file from one of the sourecforge download sites and typed tar xvzf /home/mark-williams/OperaDownloads/gaim-2.0.0beta3.1.tar.gz into the terminal, but I can't get beyond that.

I have problems with the following command lines 

cd <filename>
./configure
make
sudo make install

---

### Post by Senshi on 2006-09-07
Just open up a terminal and type in:
```
sudo aptitude update
sudo aptitude install gaim
```

---

### Post by Mark76 on 2006-09-07
Nice idea, but it installs 1.5.

Which I already have.

---

### Post by skymt on 2006-09-07
Okay, here we go. Run this command:```
gksudo gedit /etc/apt/sources.list
```Add this line to the bottom:```
deb http://repository.debuntu.org/ dapper multiverse
```Then run:```
sudo aptitude update
sudo aptitude upgrade
```That should work.

---

### Post by mishelangelo on 2006-10-13
thanx a bunch dudes...

added d new line (repository) to sources.list
sudo update
sudo upgrade
sudo apt-get install gaim

and bingo... worked like a charm!

---

### Post by dannyboy79 on 2006-10-13
> **mishelangelo said:**
> thanx a bunch dudes...

added d new line (repository) to sources.list
sudo update
sudo upgrade
sudo apt-get install gaim

and bingo... worked like a charm!

is the gaim in multiverse repo the version 2.0?

---

### Post by Mark76 on 2006-10-13
How do I install gaim-rhythmbox for gaim beta2?

---

