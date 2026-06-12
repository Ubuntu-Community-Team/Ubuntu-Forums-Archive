---
title: "How do you use g++ 4.1?"
date: 2008-05-04
forum: General Help
---

### Post by johnaintdoe on 2008-05-04
I wanted to use g++-4.1 to compile onscripter (the one in the repos is outdated), because g++ (4.2 is default in 8.04) doesn't work with the makefile.
I removed g++-4.2 and installed g++-4.1. Now, when I run configure, 

Checking C++ compiler... error

Compiler not recognised, or no compiler found.

So what do I do from here?

---

### Post by Monicker on 2008-05-04
Did you install the Ubuntu build-essential package?

---

### Post by johnaintdoe on 2008-05-04
Yes.

---

### Post by Monicker on 2008-05-04
Also check configure.log. Often that will provide more details about exactly what it was looking for.

---

### Post by Olav on 2008-05-04
You can have 4.1 and 4.2 installed on your system at the same time. There is no need to remove the later version. Then you do either

```
$ CXX="g++-4.1" ./configure
```
or
```

$ export CXX="g++-4.1"
$ ./configure

```
Then make, etc.

---

### Post by johnaintdoe on 2008-05-04
That did the trick! Thank you. I was looking for that.

---

### Post by eagleking95 on 2008-11-06
How do i install the build essential package, i mean what do i have to write in the terminal to install it? some1 tell me plz im a begginer and i need to compile my codes, cuz i need to practice for school cuz we study a bit bout ubuntu. I use xubuntu.

---

### Post by conscious on 2008-11-06
You can use one of the methods described here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) , or enter in the terminal:
```
sudo apt-get install build-essential
```

---

