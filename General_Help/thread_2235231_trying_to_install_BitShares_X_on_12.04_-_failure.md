---
title: "trying to install BitShares X on 12.04 - failure"
date: 2014-07-19
forum: General Help
---

### Post by merockstar on 2014-07-19
this is driving me absolutely nuts.

I'm trying to install BitShares X from [www.dacsunlimited.com](www.dacsunlimited.com)

I run ubuntu 12.04. I love it. I have everything set up exactly how I like it and have had for at least a year now if not longer. I don't want to upgrade. I compiled in a virtualbox, but I'd rather not have to run a virtualbox to access my wallet, it takes up so much computer power that it causes everything to drag.

here's what I've done

```

sudo apt-get install cmake git libreadline-dev uuid-dev g++ libdb++-dev libdb-dev zip libssl-dev openssl build-essential python-dev autotools-dev libicu-dev libbz2-dev libboost-dev libboost-all-dev
sudo apt-get update
sudo apt-get upgrade
git clone https://github.com/dacsunlimited/bitsharesx.git
cd bitsharesx
git checkout 0.2.0
git submodule init
git submodule update
cmake .
```

then it barked at me, "your cmake is out of date!"

okay, so per [http://www.ubuntuupdates.org/ppa/kubuntu-ppa_beta?dist=precise](http://www.ubuntuupdates.org/ppa/kubuntu-ppa_beta?dist=precise) I did this:

```

sudo add-apt-repository ppa:kubuntu-ppa/beta
sudo apt-get update
sudo apt-get upgrade

```

verified with cmake --version that I'm now running 2.8.12.1

so i tried it again
```

cmake .

```

then it barked at me, "your GCC is out of date!"

ok... so I follow the instructions here: [http://ubuntuhandbook.org/index.php/2013/08/install-gcc-4-8-via-ppa-in-ubuntu-12-04-13-04/](http://ubuntuhandbook.org/index.php/2013/08/install-gcc-4-8-via-ppa-in-ubuntu-12-04-13-04/)

```

sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update; sudo apt-get install gcc-4.8 g++-4.8
sudo update-alternatives --remove-all gcc 
sudo update-alternatives --remove-all g++
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 20
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 20
sudo update-alternatives --config gcc
sudo update-alternatives --config g++

```

then I verified that I'm now using 4.8 with gcc --version:

```

merockstar@merockstar-HP-Pavilion-dv6-Notebook-PC:~/bitsharesx$ gcc --version
gcc (Ubuntu 4.8.1-2ubuntu1~12.04) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

so i tried it again... but it still thought I was using an outdated GCC.

after a restart, it picked up on the correct version of GCC, but now it's upset because boost is outdated.

so I:

```

sudo add-apt-repository ppa:boost-latest/ppa
sudo apt-get update
sudo apt-get install libboost1.55-all-dev libboost1.55-dev

```

after deleting my bitsharesx folder and doing another:

```

git clone https://github.com/dacsunlimited/bitsharesx.git
cd bitsharesx
git checkout 0.2.0
git submodule init
git submodule update

```

It finally started to compile! I was so happy!!!!!!

then I got this at 46%:

```

/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:4:40: error: ‘HEAD’ was not declared in this scope
 #define FC_GIT_REVISION_UNIX_TIMESTAMP HEAD-HASH-NOTFOUND
                                        ^
/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:9:46: note: in expansion of macro ‘FC_GIT_REVISION_UNIX_TIMESTAMP’
 const uint32_t git_revision_unix_timestamp = FC_GIT_REVISION_UNIX_TIMESTAMP;
                                              ^
/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:4:45: error: ‘HASH’ was not declared in this scope
 #define FC_GIT_REVISION_UNIX_TIMESTAMP HEAD-HASH-NOTFOUND
                                             ^
/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:9:46: note: in expansion of macro ‘FC_GIT_REVISION_UNIX_TIMESTAMP’
 const uint32_t git_revision_unix_timestamp = FC_GIT_REVISION_UNIX_TIMESTAMP;
                                              ^
/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:4:50: error: ‘NOTFOUND’ was not declared in this scope
 #define FC_GIT_REVISION_UNIX_TIMESTAMP HEAD-HASH-NOTFOUND
                                                  ^
/home/merockstar/bitsharesx/libraries/fc/git_revision.cpp:9:46: note: in expansion of macro ‘FC_GIT_REVISION_UNIX_TIMESTAMP’
 const uint32_t git_revision_unix_timestamp = FC_GIT_REVISION_UNIX_TIMESTAMP;
                                              ^
make[2]: *** [libraries/fc/CMakeFiles/fc.dir/git_revision.cpp.o] Error 1
make[1]: *** [libraries/fc/CMakeFiles/fc.dir/all] Error 2
make: *** [all] Error 2

```

[img]http://www.millsworks.net/blog/wp-content/uploads/2009/04/writing_process.gif[/img]

can anybody help me?

---

### Post by starrysl on 2014-08-26
try to replace with [COLOR=#000000][FONT=dejavu sans mono]HEAD-HASH-NOTFOUND [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]with [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]1398967484

according to [/FONT][/COLOR]https://bitsharestalk.org/index.php?topic=4480.15

---

