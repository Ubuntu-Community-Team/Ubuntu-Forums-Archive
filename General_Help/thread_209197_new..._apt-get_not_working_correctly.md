---
title: "new... apt-get not working correctly?"
date: 2006-07-04
forum: General Help
---

### Post by thehotshxt on 2006-07-04
so i'm new to ubuntu... i've already got my wireless up and running (another hassle that i posted about)... i have very limited use of linux, and this is my first with any debian based package (fedora for basic things, not everyday desktop use)

this is probably a pretty easy question, but when i type

sudo apt-get install mplayer

output is:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer

is there some sort of configuration i need to do to set up repositories (terminology correct?) to be used?

i tried to install from source, but kept on getting an error that it needed the libpng and libpng-dev packages installed, which i proceeded to do, and install and still i get the same error when i try to "sudo ./configure --enable-gui", so i thought i could install the apt-get package?  

i have never done anything with apt-get, only compiling / building / make 

oh, and command lines are very helpful... :)

---

### Post by 23meg on 2006-07-04
You need to enable extra repositories. mplayer is in Multiverse.

[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by thehotshxt on 2006-07-04
thanks.  knew it was just unfamiliarity with this keeping me back.  much appreciated!

---

