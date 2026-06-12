---
title: "How to install .tar.gz"
date: 2008-07-06
forum: General Help
---

### Post by shantanu18 on 2008-07-06
I download a zip file ( compiz-0.6.2.tar.gz) . When double click it , it open with archive maneger>> How i can install it>> Help

---

### Post by funkydan2 on 2008-07-07
Why do you want to install compiz 0.6.2 from source?

It would be much easier if you went to 'System->Administration->Synaptic Package Manger', searched for the program you wanted to install and installed it from there.

Installing from source is a difficult process.

(Also, in Hardy/8.04 I think the version of Compiz-Fusion is 0.7.4 anyway.)

---

### Post by Phixion on 2008-07-07
Compiling from source isn't hard at all, but you should really install from the repositories if at all possible.

sudo apt-get install compiz

---

### Post by neurostu on 2008-07-07
the <something>.tar.gz is indicative of 2 things:
1 - .tar - is a tar ball, meaning all of the src files are packaged into one file a tar ball with the .tar ending
2 - .gz - gzip is a compressed version of the tar file. Shrinking it into a smaller file.


What you need to do is unzip and untar the file, you can do that by:
```

tar -xvzf <file>.tar.gz

```
or with the GUI, extract here option.

The extracted archive should contain a README file which should have some instructions...

If not the standard procedure is to run:
```

./configure

```
this prepares the source to be installed on your machine. (If configure doesn't exist you need to run ./autogen.sh which should generate it... if autogen doesn't exist read the doc that came with the tar.gz)

Next run make:
```

make

```
simply put this will compile, or turn into binary, the code.

Finally run:
```

sudo make install

```
This actually installs the program by placing all the necessary files where they need to be... (ie. putting the binaries in /usr/local/bin/)

Like funkydan2 said, its definitely better to install from the repos if you can, trust us it is a million times easier, but if you looking to learn about linux and how to "install" or "compile from source" the above instructions should suffice most of the time.

---

