---
title: "Installing programs"
date: 2008-07-06
forum: General Help
---

### Post by masoud23 on 2008-07-06
:confused:I have down loaded a program it is on my desktop an look like this:

FileZilla_3.0.11_i586-linux-gnu.tar.bz2

what is the command line at terminal for opening and installing it?

Is there program one can use that do the installation with out using terminal and writing commands in Ubuntu?

tanks in advance

---

### Post by hoooootz82 on 2008-07-06
Well to install that specific package you would have to compile it yourself, another way is to install filezilla using synaptic. This would be easier, but if you need practice compiling lets begin.

Right click the file and select extract here.

Then open a terminal and type
```
cd /home/(USERNAME)/Desktop/FileZilla_3.0.11_i586-linux-gnu
```

Next make sure you have all the dependencies and whatnot:
```
./configure
```

Now compile:
```
make
```

I forgot to mention, but I wouldnt think you have checkinstall installed, so youll want to do that:
```
sudo apt-get install checkinstall
```

Now if the ./configure command gave you no errors, you should be able to go on and install:
```
sudo checkinstall
```
and follow the prompts.

Like i said it would be much easier to use synaptic to install this program, but its good to be able to compile from the source code.

Hope this helped.

---

### Post by lamego on 2008-07-06
You are safer if you use the applications available from the repositories, FileZilla is available from Applications -> Add/Remove programs.
If for some reason you need a newer version not available on the repositories, you can search for a package on getdeb.

---

### Post by zvacet on 2008-07-06
You can read [this.]("http://monkeyblog.org/ubuntu/installing/")I think it will be helpful to you.

---

