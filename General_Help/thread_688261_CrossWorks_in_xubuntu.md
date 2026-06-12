---
title: "CrossWorks in xubuntu"
date: 2008-02-05
forum: General Help
---

### Post by MonkeyPlus on 2008-02-05
I'm installing this: 

[http://www.rowley.co.uk/msp430/index.htm](http://www.rowley.co.uk/msp430/index.htm)

on xubuntu after having succesfully installed it on normal ubuntu. However, when I run the setup programme I get the following error:

./Setup: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I checked on synaptic and I do have a version of libstdc++ installed, so I'm quite puzzled by this error.

---

### Post by kesman on 2008-02-05
You should locate the file that is needed with either locate or whereis -commands.
```

locate libstdc++.so.5

```
or
```

whereis libstdc++.so.5

```
They should point you to the directory where that file is. Then you must fix the directory in the setup-file, since apparently it's wrong in the file.

---

### Post by MonkeyPlus on 2008-02-05
Well, I've only got libstdc++.so.6 in /usr/lib and I have the feeling that won't do. Also, the setup file is an executable so it isn't a simple matter to change it.

---

### Post by kesman on 2008-02-05
Ok. Try googling around, since I have no idea why it wouldn't work under xfce when it does under gnome.

---

### Post by MonkeyPlus on 2008-02-05
Most of the stuff i can find through google is specific to redhat/fedora and isn't much use to me as it recommends installing packages which don't seem to exist in Ubuntu.

I did find this:

[http://www.joewein.de/sw/swnotes002.htm](http://www.joewein.de/sw/swnotes002.htm)

but it didn't help seeing as the files in question don't even exist in /usr/local/lib

Edit: never mind, I found a solution here [http://ubuntuforums.org/showthread.php?t=673762](http://ubuntuforums.org/showthread.php?t=673762)

There is an equivalent package i can install

---

