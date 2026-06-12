---
title: "installing to opt"
date: 2007-05-13
forum: General Help
---

### Post by Mateo on 2007-05-13
i hear all the time people say that they install programs (from source code) to the opt directory.  how do you do this. thanks.

---

### Post by zvacet on 2007-05-13
If you downloaded program in any other directory than opt(let say it is desktop) do this

```
username@localhost:~/Desktop$ sudo cp program.tar.gz /opt
```

or

```
username@localhost:~/Desktop$ sudo mv program.tar.gz /opt
```

```
cd /opt
```
 and when you are in opt

```
tar zxvf program.tar.gz
```

---

### Post by Mateo on 2007-05-13
that's not how programs install though.  to install a program you usually do:

./configure
make
sudo make install

but the sudo make install command makes it install to the /usr/bin directory and other places. so how do you make it install to the /opt directory.  thanks.

---

### Post by zvacet on 2007-05-14
Try this 

```
tar zxvf program.tar.gz -C /opt
```

---

### Post by Ken_Lewis81 on 2007-05-14
A quick googling (refreshing, I suggest you try it!) shows up a page about a unrelated package [http://www.unidata.ucar.edu/support/help/MailArchives/netcdfgroup-list/msg01062.html](http://www.unidata.ucar.edu/support/help/MailArchives/netcdfgroup-list/msg01062.html), which lists the options you have for configure.  Try a ./configure --help to read up what your program's particular config script can do.

Hope this helps.
Take care.
Ken.

---

