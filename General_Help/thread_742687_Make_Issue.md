---
title: "Make Issue"
date: 2008-04-01
forum: General Help
---

### Post by l3nny86 on 2008-04-01
Hi everyone, I have a problem and I hope I can find a solution here.

I have Ubuntu Server 7.10 running (basic install with SSL, MySQL, LAMP and I think one other). Currently I am connected to the server via SSL and everything that I am trying to get to work is working out fine till like a couple hours ago. 

What I am trying to do is install a Mangos server according to [**this**]("http://www.mangosproject.org/forum/index.php?showtopic=7730") tutorial. I am at the point where I have to run the make command to compile the program. So now this is what my cli spits out. 
```
creator@myserver:~/sources/mangos$ make
make  all-recursive
make[1]: Entering directory `/home/creator/sources/mangos'
Making all in dep
make[2]: Entering directory `/home/creator/sources/mangos/dep'
Making all in include
make[3]: Entering directory `/home/creator/sources/mangos/dep/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/creator/sources/mangos/dep/include'
Making all in lib
make[3]: Entering directory `/home/creator/sources/mangos/dep/lib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/creator/sources/mangos/dep/lib'
Making all in src
make[3]: Entering directory `/home/creator/sources/mangos/dep/src'
Making all in g3dlite
make[4]: Entering directory `/home/creator/sources/mangos/dep/src/g3dlite'
source='AABox.cpp' object='AABox.o' libtool=no \
        DEPDIR=.deps depmode=none /bin/bash ../../../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I../../..  -I. -I./../../include -I./../../include/g3dlite   -DENABLE_RA -DENABLE_CLI -DDO_MYSQL  -c -o AABox.o AABox.cpp
../../../depcomp: line 566: exec: g++: not found
make[4]: *** [AABox.o] Error 127
make[4]: Leaving directory `/home/creator/sources/mangos/dep/src/g3dlite'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/creator/sources/mangos/dep/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/creator/sources/mangos/dep'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/creator/sources/mangos'
make: *** [all] Error 2

```

I have to say that I am not a professional Linux user but neither a total n00b, but I cannot seem to be able to make sense of the error message. If anyone on here could please help me (I tried to find prior posts about this, but could not find any; so sorry if there are any).

Thx for any help.

---

### Post by Oldsoldier2003 on 2008-04-01
> **l3nny86 said:**
> Hi everyone, I have a problem and I hope I can find a solution here.

I have Ubuntu Server 7.10 running (basic install with SSL, MySQL, LAMP and I think one other). Currently I am connected to the server via SSL and everything that I am trying to get to work is working out fine till like a couple hours ago. 

What I am trying to do is install a Mangos server according to [**this**]("http://www.mangosproject.org/forum/index.php?showtopic=7730") tutorial. I am at the point where I have to run the make command to compile the program. So now this is what my cli spits out. 
```
creator@myserver:~/sources/mangos$ make
make  all-recursive
make[1]: Entering directory `/home/creator/sources/mangos'
Making all in dep
make[2]: Entering directory `/home/creator/sources/mangos/dep'
Making all in include
make[3]: Entering directory `/home/creator/sources/mangos/dep/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/creator/sources/mangos/dep/include'
Making all in lib
make[3]: Entering directory `/home/creator/sources/mangos/dep/lib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/creator/sources/mangos/dep/lib'
Making all in src
make[3]: Entering directory `/home/creator/sources/mangos/dep/src'
Making all in g3dlite
make[4]: Entering directory `/home/creator/sources/mangos/dep/src/g3dlite'
source='AABox.cpp' object='AABox.o' libtool=no \
        DEPDIR=.deps depmode=none /bin/bash ../../../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I../../..  -I. -I./../../include -I./../../include/g3dlite   -DENABLE_RA -DENABLE_CLI -DDO_MYSQL  -c -o AABox.o AABox.cpp
../../../depcomp: line 566: exec:**[COLOR="DarkRed"] g++: not found[/COLOR]**
make[4]: *** [AABox.o] Error 127
make[4]: Leaving directory `/home/creator/sources/mangos/dep/src/g3dlite'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/creator/sources/mangos/dep/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/creator/sources/mangos/dep'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/creator/sources/mangos'
make: *** [all] Error 2

```

I have to say that I am not a professional Linux user but neither a total n00b, but I cannot seem to be able to make sense of the error message. If anyone on here could please help me (I tried to find prior posts about this, but could not find any; so sorry if there are any).

Thx for any help.

g++: not found

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by l3nny86 on 2008-04-02
thx Oldsoldier2003 ... its running past that mistake ... lets see where I ll get stuck next :D

---

