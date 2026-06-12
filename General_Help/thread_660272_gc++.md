---
title: "gc++"
date: 2008-01-06
forum: General Help
---

### Post by giok13 on 2008-01-06
ive installed gc++ on ubuntu 77.10 and i want to make a bot for gaming. how do i compile stuff. i know how to use the c++ compiler on windows but i have no idea how to use the gc++. also i cant even  find the application itself. do i have to run it through the terminal? or is it like an application

---

### Post by Dodelijk on 2008-01-06
Do you mean g++ ? 

if so: 

You have to use the terminal

you have a file with your code in called say myfile.cpp and you save it
you navigate to its directory and compile/run like this 

```

g++ -c myfile.cpp            

```

which creates an object file which you make into an executable with 

```

g++ -o MyProg myfile.o

```

Which makes the executable called MyProg
which you can run from the terminal with ./MyProg

That should get you started....
I think you should look elsewhere for programming under linux, This is not really a programming board. Google "using g++" and find out how to use the terminal

---

### Post by giok13 on 2008-01-06
kk thx. yea i ment g++

---

### Post by SOULRiDER on 2008-01-06
You can just do
```
g++ file.cpp -oca.out
```

What packages did you install exactly? I suggets you install build-essential
```
sudo aptitude install build-essential
```

---

