---
title: "Newbie questions, sorry"
date: 2008-04-17
forum: General Help
---

### Post by Wantingtolearn on 2008-04-17
I am trying to install G++ and other programs through Synaptic and terminal.  I see the programs in usr/bin but when i click them they don't work.  What do i do?  Thank you ahead of time, I am sorry that I am such a novice, but I will try hard.

---

### Post by wolfen69 on 2008-04-17
you would have to launch them as root. simply typing the name of an app in the terminal will launch it. if you want root privilages put gksudo in front of the name.

---

### Post by Wantingtolearn on 2008-04-18
i am really sorry I think that I tried that, but this is what I got.

kmichaellong@kmichaellong-laptop:~$ G++
bash: G++: command not found
kmichaellong@kmichaellong-laptop:~$ /.G++
bash: /.G++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ gksudo G++
sudo: 1 incorrect password attempt
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSkmichaellong@kmichaellong-laptop:~$ .\G++
bash: .G++: command not found
kmichaellong@kmichaellong-laptop:~$ /.G++
bash: /.G++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ gksudo G++
kmichaellong@kmichaellong-laptop:~$ g++
g++: no input files
kmichaellong@kmichaellong-laptop:~$ /.g++
bash: /.g++: No such file or directory
kmichaellong@kmichaellong-laptop:~$ 


I don't know if I am doing this the rigth way, i am very new, but very interested.

Thank you so much, I think it is awesome that people are out there to help others out.

---

### Post by ad_267 on 2008-04-18
```
kmichaellong@kmichaellong-laptop:~$ g++
g++: no input files
```

Commands in the terminal are case sensitive, so this attempt worked. g++ is a c++ compiler but you didn't give it anything to compile. For info on how to use g++, type "man g++"

Some applications that you install using synaptic or apt-get will have a GUI and will be found under your applications menu, but for things like g++ that are used in the command line you just type the name of the program along with any input options required.

Here's an example of how to compile something with g++:
```
g++ source_file.cpp -o output_file
```

---

### Post by Wantingtolearn on 2008-04-18
okay I think that I get it thank you so much!!

---

