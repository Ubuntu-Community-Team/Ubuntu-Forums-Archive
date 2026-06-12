---
title: "Error trying to compile pidgin 2.3.0"
date: 2007-12-02
forum: General Help
---

### Post by Rippie on 2007-12-02
Hello guys. im trying to compile Pidgin 2.3.0 and get a error. I combined two sites when trying to do so, they get listed here.

Site 1: [http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)
Site 2: [https://help.ubuntu.com/community/Pidgin](https://help.ubuntu.com/community/Pidgin)

On site 2 there is a few things it tells me to install before i do anything else. now when i want to compile i get this error.

> checking for g++... g++
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
rippie@riplaptop:~/Desktop/pidgin-2.3.0$ 

Im using this command to compile

```
 ./configure --enable-gnutls=yes
```

I've tried a bit and search around and found some solutions, but every package i install dont seem to help. 

Hope someone can help me out.

---

### Post by monktbd on 2007-12-02
did you install the build environment package?
```
sudo apt-get install build-essential
```

---

### Post by soxs on 2007-12-02
an alternative would be to visit [www.getdeb.net](www.getdeb.net)
there you'll find a compiled version of pidgin 2.3. (I myself use it now)

---

### Post by Rippie on 2007-12-02
Yep i already tried the build-essential

> rippie@riplaptop:~$ sudo apt-get install build-essential
[sudo] password for rippie:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rippie@riplaptop:~$ 

Hmm i suppose i could try the one from getdeb, but its more fun to try to compile :)

Anyone has any suggestions ??

---

### Post by walkerk on 2007-12-02
when you configure do this
```
./configure --enable-TLS
```

I've already compiled 2.3...
```
./configure --enable-TLS
make
sudo make install
``` 

:)

---

### Post by Rippie on 2007-12-02
And it will still work with MSN ? SSL support ?

---

### Post by Rippie on 2007-12-02
oki just tried it, same result. any other ?

---

### Post by walkerk on 2007-12-02
yes it will enable TLS (an imporved form of SSL) which will allow you to log on to MSN...

ensure you have g++ installed
```
sudo apt-get install g++
```

then try again..

---

### Post by atlfalcons866 on 2007-12-02
or just go here [http://www.getdeb.net/release.php?id=1855](http://www.getdeb.net/release.php?id=1855)

its a compiled pidgin.

---

### Post by walkerk on 2007-12-02
Why are people against compiling? Just grab the necessary dependencies and compile... 

IMO getdeb keeps new users from learning...

---

### Post by Rippie on 2007-12-02
> rippie@riplaptop:~$ sudo apt-get install g++
[sudo] password for rippie:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
g++ set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rippie@riplaptop:~$ 
rippie@riplaptop:~$ 


Its already installed

---

