---
title: "libext2fs not found"
date: 2007-06-02
forum: General Help
---

### Post by diafygi on 2007-06-02
Hey everyone,

I'm sending my laptop off to get repaired, so I am trying to securely delete all my bank/personal information off of my ubuntu fiesty partition. I found a neat program called _[wipe2fs]("http://web.cecs.pdx.edu/~cklin/wipe2fs/")_ that erases or writes over all the unused or free space in a ext2 or ext3 partition. The problem is that I can't seem to get a dependency to install. I installed g++. Here are my steps:
1. untar wipe2fs to /home/user1/wipe2fs/
2. cd /home/user1/wipe2fs
3. sudo ./configure
    Output
    ```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ext2fs_open in -lext2fs... no
configure: error: libext2fs not found
    
```

I ran a search and I found that e2fslibs has libext2fs in its description. I also found two files called libext2fs.so.2 and libext2fs.so.2.4 in my /lib/ folder. So I think I have libext2fs installed, but my configure doesn't recognize it. Anyone have any suggestions?

---

### Post by zvacet on 2007-06-02
When I searched for that file with synaptic i get this

**e2fslibs** and **e2fslibs-dev**

Try to install both of them.

---

### Post by diafygi on 2007-06-04
right, I have e2fslibs and e2fsprogs installed in the synaptic package manager. So I would think that my system would know that I have the libext2fs library. I'm new to linux, so I don't know what I'm missing.

---

