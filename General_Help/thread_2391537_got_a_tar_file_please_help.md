---
title: "got a tar file please help"
date: 2018-05-10
forum: General Help
---

### Post by arshd33p on 2018-05-10
i just downloaded, a tar.dz file from broadcom.com.
but i dont know how to intall it.
i am a new bie.
working with Ubuntu 14.04.5 LTS  and wifi isnt working.
it shows the name of wifi, but cant connect to wifi.
this is the file i downloaded :[https://docs.broadcom.com/docs/12358410](https://docs.broadcom.com/docs/12358410)
please help.
any kind of help in 10 minutes will be appriciable.

---

### Post by yancek on 2018-05-10
> i just downloaded, a tar.dz

No, you didn't.  You downloaded a "tar.gz" file, proof read your posts before posting them.

If you want to do it from a terminal. first change to the diretory in which you have the file, Downloads?  Read the link below which gives you the command and explains what it does.
You can also do it in a file manager by right clicking and selecting one of the extract options.

[https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file](https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file)

---

### Post by oldos2er on 2018-05-10
Moved to General Help.

---

### Post by spjackson on 2018-05-10
That tar.gz contains source code which you need to compile and install.

What you need to do in a terminal is this.
1. Extract the archive e.g.
```

mkdir foo
cd foo
tar xzf ../hybrid-v35_64-nodebug-pcoem-6_30_223_271.tar.gz

```
2. Read the licence, e.g.
```

less lib/LICENSE.txt

```
3. Build and install the software.
```

make
sudo make install

```

---

### Post by arshd33p on 2018-05-12
> **spjackson said:**
> That tar.gz contains source code which you need to compile and install.

What you need to do in a terminal is this.
1. Extract the archive e.g.
```

mkdir foo
cd foo
tar xzf ../hybrid-v35_64-nodebug-pcoem-6_30_223_271.tar.gz

```
2. Read the licence, e.g.
```

less lib/LICENSE.txt

```
3. Build and install the software.
```

make
sudo make install

```
thanks that was really helpful.

---

