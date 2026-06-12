---
title: "Problems installing Leelachess-0.29."
date: 2023-01-09
forum: General Help
---

### Post by cuasito on 2023-01-09
Hi,

Trying to install/run Leelachess-0.29 

[https://github.com/LeelaChessZero/lc0/blob/master/README.md#linux](https://github.com/LeelaChessZero/lc0/blob/master/README.md#linux) 

```
sudo apt-get install libstdc++-8-dev clang-6.0 ninja-build pkg-config
pip3 install meson --user
CC=clang-6.0 CXX=clang++-6.0 INSTALL_PREFIX=~/.local ./build.sh
```

*These are instructions for 18 my system is Ubuntu 22 LTS, so i just updated the versions ...

In Scid; after the compilation/installation: 

I am not able to find the path in order to run the app, right now this is how it is: /home/user/lc0/build/release/lco but it do not work, do not play chess, it looks like i did not find the right path. Any idea?.

Thanks for any advice.

EDIT: I tried in many ways ...

---

