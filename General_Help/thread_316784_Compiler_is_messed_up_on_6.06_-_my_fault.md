---
title: "Compiler is messed up on 6.06 - my fault"
date: 2006-12-11
forum: General Help
---

### Post by 9o1 on 2006-12-11
```
root@octane:/home/wt409863/nmap-4.20# ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```The repository has Nmap 4.03, I want 4.20. This is why I'm trying to compile instead of doing the easy method of installing via apt. Any idea as to what's wrong with my compiler setup?

---

### Post by musicinmybrain on 2006-12-11
It says "See `config.log' for more details."

What does config.log say?

I don't know how used to compiling things you are, but try "sudo apt-get install build-essential" to make sure you have a complete basic toolchain installed.

---

### Post by 9o1 on 2006-12-11
> **musicinmybrain said:**
> It says "See `config.log' for more details."

What does config.log say?

I don't know how used to compiling things you are, but try "sudo apt-get install build-essential" to make sure you have a complete basic toolchain installed.Now its getting somewhere. We'll see if it compiles and installs all the way. Thx.

---

### Post by 9o1 on 2006-12-11
> **musicinmybrain said:**
> It says "See `config.log' for more details."

What does config.log say?

I don't know how used to compiling things you are, but try "sudo apt-get install build-essential" to make sure you have a complete basic toolchain installed.The first time I tried after installing I was root so the make install (step 3) failed. The next time I did the ./configure and make as a regular user (steps 1 and 2) and the make install (step 3) as root and it worked fine. Thanks for the help.

---

