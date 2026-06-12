---
title: "Compiling Battle for Wesnoth Source for Ubuntu"
date: 2007-05-30
forum: General Help
---

### Post by DarKnyht on 2007-05-30
I have recently become addicted to Battle for Wesnoth, but have run into frustration as the 1.2.3 build that is available has problems.  There is a newer version out, but the Ubuntu library has yet to release it.  I am interesting in trying to install myself, but being a new Ubuntu user I have no clue where to start

Can anyone explain how the process works?

---

### Post by stadt on 2007-05-30
get the ready to use compiled ones here (there are other nice games too)

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by Snargle on 2007-06-03
It is really rather simple. You need  a bunch of tools and header files. To get these type:
```
sudo apt-get build-dep wesnoth
```
remove the old version:
```
sudo apt-get remove wesnoth
```
Then, get the wesnoth source from the website. 'cd' to the unpacked directory and type:
```

./configure
make
sudo make install
wesnoth

```

---

### Post by hanzj on 2007-06-03
> **Snargle said:**
> It is really rather simple. You need  a bunch of tools and header files. To get these type:
```
sudo apt-get build-dep wesnoth
```

When I do that, I get an error message:
> E: You must put some 'source' URIs in your sources.list

---

### Post by hanzj on 2007-06-03
I got the "get the ready to use compiled ones here" that Stadt pointed to. I downloaded all the debs and then, in terrminal did 
sudo dpkg -i wesnoth_filename.deb to each deb file. But when i started wesnoth from the menu, the main screen of wesnoth still says 1.2.3 in the lower left corner. What's wrong?

---

