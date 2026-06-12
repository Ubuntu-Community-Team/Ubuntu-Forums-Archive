---
title: "Boost 1.37 Install"
date: 2017-09-12
forum: General Help
---

### Post by sicxnull on 2017-09-12
Hoping I can get some help. 

I'm attempting to install Boost 1.37 on 16.04LTS but keeping hitting a wall. Following these instructions [https://ubuntuforums.org/showthread.php?t=1180792](https://ubuntuforums.org/showthread.php?t=1180792)

i get stuck at:

[COLOR=#000000]Firstly, you will not want to compile the [/COLOR][I]whole boost library since that means compiling a lot of libraries that you don't want or wont use. So, to see a list of the libraries that need compiling, run:
Code:

[/I][I]./bootstrap.sh --show-libraries
[/I][I][COLOR=#000000]
[/COLOR][/I]
What i'm getting 

null@ubuntu:~/Downloads$ tar xjf boost_1_37_0.tar.bz2
null@ubuntu:~/Downloads$ cd ./boost_1_37_0
null@ubuntu:~/Downloads/boost_1_37_0$ ./bootstrap.sh --show-libraries
bash: ./bootstrap.sh: No such file or directory


There is no bootsrap.sh in the directory. I've downloaded the source from multiple locations and same thing every time. What am i missing?

---

