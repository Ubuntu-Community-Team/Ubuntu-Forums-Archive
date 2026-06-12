---
title: "How to open RAR5 files in ubuntu?"
date: 2019-02-18
forum: General Help
---

### Post by jebi on 2019-02-18
hi,

i frequently have to open a windows 7 vm with winrar 5 installed just to open rar5 files..

1. I was wondering how you install rar v 5 in ubuntu the s/f center version only opens rar4.  how do you update it to version 5? could someone write an step by step idiots guide? i would prefer to not use the cmdline to open rars would like to use archive manager app gui?

2.  would some tell me an idiots guide to running winrar 5 in wine?

many mny thx to anyone who helps.

thx

---

### Post by Holger_Gehrke on 2019-02-18
What version of Ubuntu are you using ? On Ubuntu 18.04 there's a command line unrar in the repositories that gives as it's version information
```
UNRAR 5.50 freeware      Copyright (c) 1993-2017 Alexander Roshal
```
If that is installed, the archive manager should use it to unpack rar-files (At least if the archive manager is still file-roller, which actually doesn't handle any archives itself and just calls the respective command-line tools to do their job).

Holger

---

### Post by jebi on 2019-03-10
thx  could you tell me how to update the repository or add the newest repository for rar and unrar?  also how to check what version is installed?  thx

---

### Post by Holger_Gehrke on 2019-03-11
Repositories are tied to the release of Ubuntu you're running. There are two 'unrar' packages in the repositories, 'unrar-free' (in universe/utils) and 'unrar' (in 'multiverse/utils). 'unrar-free' is AFAIK a clean-room reimplementation, meant to be a truly free version of unrar, which seems to be stuck at compatibility with version 2. The package 'unrar' is the 'official' RARlabs unrar, which has a slightly strange license (which is the reason for the existence of the other one; basically: you get source, you can use it as you want, but you may not use the source to reverse engineer a compressor for rar).

To check the installed version, open a terminal and enter
```
dpkg-query -l 'unrar*'
```
this should show you both packages, their versions and whether or not they are installed. If you have only the free version installed, a simple ```
sudo apt install unrar
```will get you the other. You will then have two unrar's, named unrar-free and unrar-nonfree; you can use 'sudo update-alternatives --config unrar' to switch which one gets used if you call 'unrar'.

Holger

---

